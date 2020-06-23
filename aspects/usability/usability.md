# Usability

If your program returns a zero, you are a hero! If your program returns a one, it means something went wrong. But _what_ did go wrong? Make sure that your program always returns a correct value in case something goes wrong: 0 indicates success and everything unsuccessful is denoted by non-zero values. Also make sure your program provides proper feedback in case the user does not provide correct arguments or inputs. The next time the user runs your program, you want to make sure that the user understands how to use it! Sometimes it might be better to reprompt the user for input.

The process wherein a program detects a serious error condition and handles it is also called a "gracefull exit". The code associated with a graceful exit may also take additional steps, such as closing files, to ensure that the program leaves data in a consistent, recoverable state.

Below you can find some examples of how to implement this correctly.

    if (argc != 2)
    {
        fprintf(stderr, "Usage ./vigenere key");
        return 1;
    }

    for (int i = 0; i < strlen(key); i++)
    {
        if (!isalpha(key[i]))
        {
            fprintf(stderr, "Key must be entirely alphabetical.");
            return 1;
        }
    }
