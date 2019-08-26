Merchant Address: n1s7DwSZ4nSh471iPhAGZZbXkiTvtQCi5B
Customer Address: miGm4kNffG2vfwM4H1JETFhFaPoXKsCDrP

Self Signed Keys generated via The following commands. Below directions intended to also be used with android phone.

Create an auxiliary file “android_options.txt” with this line inside:
basicConstraints=CA:true

Create self-signed certificate using these commands:
openssl genrsa -out priv_and_pub.key 2048
openssl req -new -days 3650 -key priv_and_pub.key -out CA.pem
openssl x509 -req -days 3650 -in CA.pem -signkey priv_and_pub.key -extfile ./android_options.txt -out CA.crt
Now our CA.crt certificate is almost ready.

Convert certificate to DER format:
openssl x509 -inform PEM -outform DER -in CA.crt -out CA.der.crt
Import CA.der.crt:
Put the CA.der.crt onto the sdcard of your Android device (usually to internal one). It should be in root directory.
Go to Settings / Security / Credential storage and select “Install from device storage”.
The .crt file will be detected and you will be prompted to enter a certificate name.
After importing the certificate, you will find it in Settings / Security / Credential storage / Trusted credentials / User.
