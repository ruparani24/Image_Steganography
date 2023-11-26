# Image_Steganography
Steganography is the art of hiding secret data in any image.

ENCODING :

For each character in the data, its ASCII value is taken and converted into 8-bit binary [1].
Three pixels are read at a time having a total of 3*3=9 RGB values. The first eight RGB values are used to store one character that is converted into an 8-bit binary.
The corresponding RGB value and binary data are compared. If the binary digit is 1 then the RGB value is converted to odd and, otherwise, even.
The ninth value determines if more pixels should be read or not. If there is more data to be read, i.e. encoded or decoded, then the ninth pixel changes to even. Otherwise, if we want to stop reading pixels further, then make it odd.

Example
Suppose the message to be hidden is ‘Hii’.

The message is of three bytes, therefore, the pixels required to encode the data are 3 x 3 = 9. Consider a 4 x 3 image with a total of 12 pixels, which are sufficient to encode the given data.

[(27, 64, 164), (248, 244, 194), (174, 246, 250), (149, 95, 232),
(188, 156, 169), (71, 167, 127), (132, 173, 97), (113, 69, 206),
(255, 29, 213), (53, 153, 220), (246, 225, 229), (142, 82, 175)]

DECODING :

Again, three pixels are read at a time. The first 8 RGB values give us information about the secret data, and the ninth value tells us whether to move forward or not.
For the first eight values, if the value is odd, then the binary bit is 1, otherwise it is 0.
The bits are concatenated to a string, and with every three pixels, we get a byte of secret data, which means one character.
Now, if the ninth value is even then we keep reading pixels three at a time, or otherwise, we stop.

Let’s start reading three pixels at a time.

Consider our previously encoded image.

[(26, 63, 164), (248, 243, 194), (174, 246, 250), (148, 95, 231),
(188, 155, 168), (70, 167, 126), (132, 173, 97), (112, 69, 206),
(254, 29, 213), (53, 153, 220), (246, 225, 229), (142, 82, 175)]
