This file is based on Baeldung's spring security tutorial.
I'll use Spring Data JPA and a Postgresql Database.


# Create a User model

```java

@Entity
@Table(name="users") // In Postgres db, 'user' is the table with your db's users informations
Class User(){
	@Id
	@GeneratedValue
	@Column(name="userid") private UUID userId;
	private String username;
	private String password;
	@Column(name="isenable") private boolean isEnabled;
	private String role;

	// Class Constructor (Empty and with parameters)
	// Boilerplates
	// toString method
}

``` 

# Create the UserRepository

```java 

public interface UserRepository extends JpaRepository<User, UUID> {

	// Make sure to write users, and not user.
	@Query(value="SELECT * FROM users WHERE username = ?1" nativeQuery = true)
	User getUserByUsername(String username);
}

```

# Create the User DTO (UserDetails)

```java 

// Don't name the class UserDetails or you'll get compiler error.
// If you're using IDEA, the IDE will propose to spawn the different methods, leaving you to fill them.
public class MyUserDetails implements UserDetails {

	private User user;

	public MyUserDetails(User user){
		this.user = user;
	}

	 @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        SimpleGrantedAuthority authority = new SimpleGrantedAuthority(user.getRole());
        return Arrays.asList(authority);
    }

    @Override
    public String getPassword() {
        return user.getPassword();
    }

    @Override
    public String getUsername() {
        return user.getUsername();
    }

    public String getName(){
        return user.getName();
    }

    @Override
    public boolean isAccountNonExpired() {
        return true;
    }

    @Override
    public boolean isAccountNonLocked() {
        return true;
    }

    @Override
    public boolean isCredentialsNonExpired() {
        return true;
    }

    @Override
    public boolean isEnabled() {
        return true;
    }
}

```

# Implementations of the User Details Service

```java 

public class UserDetailsServiceImpl implements UserDetailsService {

	@Autowired
	private UserRepository userRepository;

	@Override
	public UserDetails loadUserByUsername(String username) throws UserNameNotFoundException {

		User user = userRepository.getUserByUsername(username);
		if (user == null){
			throw new UserNameNotFoundException("Could not found user in database.")
		}
		return new MyUserDetails(user);
	}
}

```

# Configuring Spring Security

```java

@Configuration
@EnableWebSecurity
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {

	@Bean
	public UserDetailsService userDetailsService() {
		return new UserDetailsServiceImpl();
	}

	@Bean
	public BCryptPasswordEncoder passwordEncoder() {
		return new BCryptPasswordEncoder();
	}

	@Bean
	public DaoAuthenticationProvider authenticationProvider(){
		DaoAuthenticationProvider authenticationProvider = new DaoAuthenticationProvider();
		authenticationProvider.setUserDetailsService(userDetailsService());
		authenticationProvider.setPasswordEncoder(passwordEncoder());
		return authenticationProvider;
	}


	@Override
	protected void configure(HttpSecurity httpSecurity) throws Exception {
		httpSecurity
			.authorizeRequests()
				.antMatchers( /* Paths here */ ).permitAll() // All users could have access of this list of path
				.antMatchers(/* Paths here */ ).authenticated() // Paths accessible for authenticated users only.
				.anyRequest().authenticated()
			and()
				.formLogin().loginPage("/login") // URL to send the login form
				.loginProcessingUrl("/login") // URL when loging in
				.defaultSuccessUrl("/").permitAll() // If successful, will return to the home page, if not, will return to /login?error
			.and()
				.logout()
					.logoutRequestMatcher(new AntPathRequestMatcher("/logout")) // path to logout
					.logoutSuccessUrl("/login?logout") // Replace with the view you want the user to see after logging out.
					.deleteCookies("JSESSIONID") // Will delete the session's cookie.
					.permitAll();
	}


	// In order for your templates to have access to css and other resources, you need to whitelist the relative path.
	@Override
	public void configure(WebSecurity webSecurity) throws Exception{
		webSecurity
		.ignoring()
		.antMatchers("/resources/**", "/css/**","/icon/**", "/photo/**", "/js/**");
	}

}

```



