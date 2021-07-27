Spring Security uses BCryptPasswordEncoder. When login, the framework will take care of it, but to register, you'll need to uses the BCryptPasswordEncore.

# Encode
Simple password encoder. 

```java

public String encodePassword(String rawPassword){
    BCryptPasswordEncoder passwordEncoder = new BCryptPasswordEncoder();
    return passwordEncoder.encode(rawPassword);
    // The string will contained the passwordEncoded and the salt.
}

```

# Comparing passwords
In the case of the users wants to change something security critical, like their password, you might want them to give you their password.

```java 
// currentPassword is the password typed and should be identical the user's password in the database.
public void updatePassword(User user, String currentPassword, String newPassword){
    BCryptPasswordEncoder passwordEncoder = new BCryptPasswordEncoder();

    // The salt of the password in the database is contained in the String.
    // The encoder will apply the salt to currentPassword and will return true if it matches.
    if (passwordEncoder.matches(currentPassword, user.getPassword())) {
        user.setPassword(passwordEncoder.encode(newPassword)); // Encodes the new password and give it to the User object
        userRepository.save(user); // Save the user updated in the database.
        // Success
    } else {
        // Failed - Password typed and Password in db are different.
    }
}

```