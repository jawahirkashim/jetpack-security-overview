# jetpack-security-overview
 Encrypt/Decrypt Data on Android With Jetpack Security



 Note:
 key management:
1. generate a key by using MasterKey class

		MasterKey class: it also take care of:
		key management 
		generate key:
		eg: MasterKey.Builder(this).setKeyScheme(MasterKey.KeyScheme.AES256_GCM).build()



Android Keystore system: 
	store key in a container

	then , these key can be used for cryptographic operation



-------------------------------------------------------------------------------
two additional options for increasing key security:

1.separate hardware module.
	
 	API 28, or higher.
 	setRequestStrongBoxBacked to "true"
 
2.Restrict key usage until the user authenticates via biometrics.

	setUserAuthenticationRequired to "true"

--------------------------------------------------------------------------------
Biometric prompt:

	BiometricPrompt( onAuthenticationSucceeded(result){
	.........
	});



---------------------------------------------------------------------------------
Encryption: 

1. Encrypt files:
--------------
val encryptedFile = EncryptedFile.Builder(file,masterKey,encrytion scheme).build()


To write into the file, use openFileOutput:

	encryptedFile.openFileOutput().apply { write(password)}

To read from the encrypted file:

	password = encryptedFile.openFileInput().bufferedReader().readText()



2. Encrypt SharedPreferences: store smaller data securely

------------------------------------------------------------------------------------

