Steghide is a command-line tool used for embedding and extracting data in various kinds of files, also known as steganography. Steganography is the practice of concealing messages or information within other non-secret data to avoid detection. Steghide specifically focuses on hiding data within image and audio files. It encrypts the data before embedding it into the carrier file, making it suitable for secure communication and covert data transfer.

---
## Discover

If you want to get information about the file apply the next command:

`steghide --info image.jpg`


To extract any secret information from a file image we run the next command:

`steghide --extract -sf imagen.jpg`

---
## Hide

If you want to hide information on a file you can apply the next command:

`steghide embed -cf image.jpg -ef secret.txt`

- -ef: the text that you want to hide
- -cf: the image that is going to hide the information

---

## Machines that use this tool

- [[Amor]]