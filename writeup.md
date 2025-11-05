# EE 250 Lab 9

## Team Members 

Rida Faraz

Leyaa George

## Questions

**Question 1a: What type of authentication are we using here (currently)? Does it use any keys?**

By completing the steps to enable HTTPS and add the correct credentials for InfluxDB, we are using username and password based authentication. As long as I have the correct password, corresponding to my username, I am able to access the resource, which in this case is InfluxDB. This form of authentication does not require any keys. The password and username are the only required aspects. 

**Question 1b: Both TLS (encryption) and crypto authentication use public-private key pairs. For TLS encryption what keys are used when the client sends a message to the server? For crypto authentication, explain how the server can verify a message is from a given client?**

For TLS encryption, the new required key is the session encryption key, or symmetric key. The process starts with a server presenting its public key certificate. Then, the client verifies the certificate, and both the client and server come up with a symmetric key that will be used to encrypt the data shared between them. So, on top of the private/public key pair, the symmetric key is what allows for secure data transfers between the client and server.

In crypto authetntication, the server can verify that a message is from a given client using another set of keys. A client has its own private key that can be verified by a server using that client's public key. The client signature using the private key is what essentially enables its verification. 

**Question 2: Here we created a pair of asymmetric keys. What are their names? Which one is the public key and which one is the private key?**

The asymmetric key pair that we created includes the server.crt and server.key. The server.crt is the public key, or the public certificate, that is sent to the client by the server. The server.key is the private key and is never shared by the server.

**Question 3: What is a certificate authority (CA) for public keys? What kind of attack can a CA prevent?**

A certificate authority for public keys is an authentication service that verifies the identities of servers and other organizations. These third party services are crucial for generating the digital certificate that binds a server's public key to its verified identity. It is crucial for authentication, as the CA is able to verify that a server's public key truly belongs to the server, and the client is then able to verify the authenticity by using a CA public key to verify the digital certificate created by the CA. 

A CA can prevent Man-in-the-Middle attacks. A malicious individual can try to intercept connections by attempting to act as a server and binding their own key to the server identity. If digital certificates were not provided, then the client has no way of knowing that the server attempting to form a connection is not in fact the server that it claims to be. However, with certificates, the fake public key will be detected and the malicious server, or "man in the middle", will not be incorrectly verified. 


