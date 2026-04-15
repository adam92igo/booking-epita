error id: file://<WORKSPACE>/src/main/java/dev/_xdbe/booking/creelhouse/infrastructure/configuration/SecurityConfiguration.java:_empty_/User#builder#username#password#
file://<WORKSPACE>/src/main/java/dev/_xdbe/booking/creelhouse/infrastructure/configuration/SecurityConfiguration.java
empty definition using pc, found symbol in pc: _empty_/User#builder#username#password#
empty definition using semanticdb
empty definition using fallback
non-local guesses:

offset: 2239
uri: file://<WORKSPACE>/src/main/java/dev/_xdbe/booking/creelhouse/infrastructure/configuration/SecurityConfiguration.java
text:
```scala
package dev._xdbe.booking.creelhouse.infrastructure.config;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configurers.AbstractHttpConfigurer;

import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.provisioning.InMemoryUserDetailsManager;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.session.web.http.CookieSerializer;
import org.springframework.session.web.http.DefaultCookieSerializer;
import static org.springframework.security.config.Customizer.withDefaults;

@Configuration
@EnableWebSecurity
public class SecurityConfiguration {

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        return http
            .authorizeHttpRequests(auth -> auth
                // Step 4a: add access control
                // ...
                // Step 4a: end
                .anyRequest().permitAll()
            )
            // Step 4b: Add login form
            // ...
            // Step 4b: End of login form configuration
            
            .csrf((csrf) -> csrf
                .ignoringRequestMatchers("/h2-console/**")
            )
            .headers(headers ->
                headers.frameOptions(frameOptions ->
                    frameOptions.disable()
                )
            )
            .build();
    }

    // Step 3: add InMemoryUserDetailsManager
    @Bean
    public UserDetailsService userDetailsService() {
        UserDetails administrator = User.builder()
        .username("admin")
        .pas@@sword("{bcrypt}$2b$12$5rS8q4MzfqtxdB9vWoWL4.Ec1ro3xvEI5XE8hm7d3mes31lTFdiEG")
        .roles("ADMIN")
        .build();

    UserDetails guest = User.builder()
        .username("guest")
        .password("{bcrypt}$2b$12$DRtDHQobzWbXcW57UKsLHOSMULePWHNZG6gAXwmy2YocVZ23rn146")
        .roles("GUEST")
        .build();

    return new InMemoryUserDetailsManager(administrator, guest);
}
    // Step 3: end

}
```


#### Short summary: 

empty definition using pc, found symbol in pc: _empty_/User#builder#username#password#