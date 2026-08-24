---
title: "Advanced Caesar Cipher"
categories: [English, en-design]
tags: [design]
lang: en
---

Advanced Caesar Cipher (Caesar Cipher Plus) is a personal encryption concept intended solely for entertainment purposes; please do not use this method in high-risk situations.

This method is based on the Caesar cipher: each letter in the plaintext is shifted by a certain number of positions in the alphabet. However, the difference with this method is that the shift increases linearly, forming a cycle.

## Positioning
This method is intended only for low-risk scenarios. Like the Caesar cipher, it ensures that anyone who happens to come across it will be unable to read it and will simply ignore it.

Because the Caesar cipher is too simple, anyone with basic mental arithmetic skills can decipher the ciphertext. This method therefore builds on the Caesar cipher to make it more secure, so that unless the person who finds it is genuinely interested and takes the time to analyse it using draft paper or a computer, they will simply discard it as gibberish.

Essentially, the design philosophy is to maximise the cost to a cryptanalyst whilst maintaining the simplicity of the encryption. At the same time, it is not designed to prevent computers.

## Encryption logic
- Set the initial step size (1 to alphabet size - 1) and the alphabet.
- Starting from the first letter of the plaintext, look it up in the alphabet and count forwards by the step size set; if you reach the end, start again from the first letter of the alphabet; the letter you finally reach is the ciphertext.
- After encrypting a letter, add 1 to the step size. If the step size equals the size of the alphabet, set it to 1.
- And so on, until the complete ciphertext is obtained.
- To decrypt, simply follow the same steps, but count backwards each time.

## Points to note
The alphabet is a variable. You can use the standard alphabet, the QWERTY keyboard sequence, or you can randomise it. You can also add characters (like numbers).

To prevent others who know this method from deciphering the message, the alphabet can be randomly shuffled and used as a 'key'. As the number of possible permutations is enormous (approximately $$26!$$), it is impossible to crack by brute force, meaning that a decryptor would have to carry out specialist cryptographic analysis.

To guard against known plaintext attacks, you should avoid using fixed phrases and revealing plaintext fragments. You should also keep your expressions as concise as possible.

Since the actual key consists of the alphabet, in theory it would not matter much even if the initial step size were revealed directly. After all, there are only 25 possibilities in any case.

## Transcription method
If you wish to withstand basic cryptanalytic attacks, you might refer to the transcription rules used by Germany during the Second World War. Applying this technique before encryption blurs the boundaries between words, making it impossible to deduce the content from the structure alone.
- Space: omit
- Punctuation`.`: `X`
- Comma`,`: `Y`
- Question mark`?`: `UD`

## Storing the alphabet
To store the alphabet, you can use a rectangular table with two letters per row. This makes it easy to carry and look up.

When checking the table, divide the current step count by 2. Count downwards by the number of steps resulting from the division; if the number of steps is odd, take one more step forwards. If you go over, remember to start a new line and repeat the loop.

## Vulnerability: The plaintext and ciphertext will never be the same
In the original design, the period of the step size was restricted to the range '0 to the size of the alphabet -1', but it is now set to '1 to the size of the alphabet -1', making it impossible for the plaintext to match the ciphertext.

This design is generally considered a vulnerability in cryptography, as the fact that plaintext and ciphertext are never identical makes it easy to apply a process of elimination. This allows one to quickly rule out any possibility of plaintext and ciphertext containing the same letters.

However, this vulnerability was introduced to safeguard another design choice: the ability to disclose the initial step size.

In practice, whilst the alphabet key can simply be passed on in a note, the initial step size is difficult to share. In order to tie all security to the alphabet, I believe it is essential that the initial step size can be disclosed directly.

In the original cycle, assuming a 26-letter alphabet, one in every 26 letters is plaintext. If a cryptanalyst obtains the initial step size, they can pinpoint all the plaintext fragments, resulting in a security leak.

At the same time, if the cryptanalyst knows the initial step size, they can just as quickly rule out any possibility that the plaintext and ciphertext contain the same letters at non-zero step positions. In fact, even without knowing the initial step size, a cryptanalyst can rule out the possibility of more than one ciphertext matching the plaintext within 26 characters (one cycle).

This is therefore a trade-off made to ensure that the initial step size can be disclosed.
