Trilium is meant to store all kinds of data - including potentially sensitive data like journals or credentials etc.

For such sensitive data Trilium can protect these notes which essentially means:

* encrypting the note with encryption key based on your password. 
    * This means that without your password, protected notes are not decipherable so even if somebody managed to steal your Trilium [[document|Document]], your protected notes could not be read.
* time-limited access to protected notes
    * To first access protected notes you need to enter your password which will decrypt the note and allow you to read / write them. But after certain time period (by default 10 minutes) this decrypted note is unloaded from memory and to read it again you need to enter your password again.
    * This protects against a possible scenario where you leave your computer unlocked for a long time and somebody can access your Trilium application.
    
## How to use protected notes

Notes are by default unprotected. If you want your note to be protected, click on shield icon next to the note title as seen here:

[[gifs/protecting-note.gif]]

You can also notice how protected notes are greyed in the note tree and given subtle shield background in the note editor so you have good overview of what's protected and what isn't.

## What is encrypted

In principle Trilium encrypts data, but doesn't encrypt metadata. This specifically means:

Encrypted:
* note title
* note content
* images
* file attachments

Not encrypted:
* structure of the notes - i.e. you can still see that there are protected notes.
   * there's no attempt to hide the fact there are encrypted notes
* various metadata - e.g. date of last modification
* [[attributes]]

## Encryption details

... how we get from password to decrypted note:

1. User enters password
2. Password is put into [scrypt](https://en.wikipedia.org/wiki/Scrypt) algorithm together with "password verification" [salt](https://en.wikipedia.org/wiki/Salt_(cryptography)) to verify that password is correct
3. Password is put into scrypt algorithm together with "encryption" salt which produces a hash
    * here we use scrypt for [key stretching](https://en.wikipedia.org/wiki/Key_stretching)
4. Hash produced in the last step is used to decrypt actual _data encryption key_
    * data encryption key is encrypted with [AES-128](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) with random [IV](https://en.wikipedia.org/wiki/Initialization_vector)
    * data encryption key is random key generated at the time of [[document|Document]] initialization and is constant over the lifetime of the document. If we change password, we re-encrypt only this key.
5. We use data encryption key to decrypt actual data - note title and content.
    * encryption used is again AES-128 with [CBC chaining](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation). IV is primary key (noteId for notes and noteHistoryId for history items)