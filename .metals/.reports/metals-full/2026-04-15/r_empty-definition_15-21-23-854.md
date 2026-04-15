error id: file://<WORKSPACE>/src/main/java/dev/_xdbe/booking/creelhouse/infrastructure/persistence/CreditCardConverter.java:java/lang/String#
file://<WORKSPACE>/src/main/java/dev/_xdbe/booking/creelhouse/infrastructure/persistence/CreditCardConverter.java
empty definition using pc, found symbol in pc: java/lang/String#
empty definition using semanticdb
empty definition using fallback
non-local guesses:

offset: 1088
uri: file://<WORKSPACE>/src/main/java/dev/_xdbe/booking/creelhouse/infrastructure/persistence/CreditCardConverter.java
text:
```scala
package dev._xdbe.booking.creelhouse.infrastructure.persistence;


import javax.crypto.IllegalBlockSizeException;
import javax.crypto.BadPaddingException;
import javax.crypto.NoSuchPaddingException;
import java.security.InvalidKeyException;
import java.security.NoSuchAlgorithmException;

import jakarta.persistence.AttributeConverter;
import jakarta.persistence.Converter;
import org.springframework.beans.factory.annotation.Autowired;

import dev._xdbe.booking.creelhouse.infrastructure.persistence.CryptographyHelper;


@Converter
public class CreditCardConverter implements AttributeConverter<String, String> {

    @Autowired
    private CryptographyHelper cryptographyHelper;

    @Override
    public String convertToDatabaseColumn(String attribute) {
        // Step 7a: Encrypt the PAN before storing it in the database
        return CryptographyHelper.encryptData(attribute);
        // Step 7a: End of PAN encryption
    }

    @Override
    public String convertToEntityAttribute(String dbData) {
        // Step 7b: Decrypt the PAN when reading it from the database
        @@String pan = dbData;
        // Step 7b: End of PAN decryption
        String maskedPanString = panMasking(pan);
        return maskedPanString;
    }

    private String panMasking(String pan) {
        // Step 6:
        return pan.substring(0, 4) + "*".repeat(pan.length() - 8) + pan.substring(pan.length() - 4);
        // Step 6: End
    }

    
}
```


#### Short summary: 

empty definition using pc, found symbol in pc: java/lang/String#