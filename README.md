# kaggle_ciphertextIII
Kaggle comp


# What terms should I be aware of?
A cipher is an algorithm that transforms a readable piece of information into an unreadable one (and in most cases vice versa). Modern encryption algorithms - AES, DES, etc. - are examples of commonly used ciphers.

In this case, we've used simple (or classic) ciphers. For as long as information has existed, methods have been used to obscure the information's meaning. Before computers were common, they usually consisted of a series of simple operations performed on text. In this data you'll encounter multiple text-transformation ciphers that date back centuries, if not longer.

There is also a newer, well-known cipher that also consists of a series of simple operations performed on data.

Text that has been encrypted is referred to as ciphertext. (Unencrypted text is usually called plaintext.)

The exact cipher(s) used to encrypt this data will be revealed at the end of the competition - if they're not discovered first!

# How has the text been encrypted?
Each document has been encrypted with up to 4 layered ciphers (ciphers 1, 2, 3, and 4). We've used a difficulty value here to denote which ciphers were used for a particular piece of text.

Every document in the dataset has been padded to the next hundred characters (95->100, 213->300) with random (in-alphabet) characters, then encrypted based on its difficulty level. A difficulty of 1 means that only cipher #1 was used. A difficulty of 2 means cipher #1 was applied, followed by cipher #2, and so on. The difficulty level denotes exactly which ciphers were applied, and in what order.

To avoid issues with reproducing the plaintext (some cleaning was required to remove spurious characters), the plaintext is provided in training.csv.

# What files do I need?
You'll need training.csv and test.csv. sample_submission.csv contains the same Ids that test.csv does.

# What should I expect the data format to be?
Each row in training.csv provides the text of a line from a Shakespeare play and the index values you need to predict / match, while test.csv provides the corresponding ciphertext and difficulty levels.

# What am I predicting?
The target is a unique identifier (index) for each piece of ciphertext. Each piece of ciphertext must be matched with its corresponding piece of plaintext. To assign ciphertext_id ID_0827e580b to the line of Shakespeare with an index of 10, our prediction would look like this:

ID_0827e580b,10

# File descriptions
training.csv - the training data - contains plaintext_ids and text samples for each Shakespearean line in the training set, along with a unique index.   
test.csv - the test data - ciphertext_ids, ciphertext, and a difficulty level indicating which ciphers were used.   
sample_submission.csv - a sample submission file in the correct format.   

## Training data fields
plaintext_id - A unique ID for each line in the set.
text - The unpadded, unencrypted text of the review.
index - A unique ID that should be assigned to each ciphertext_id in test.csv when you've decrypted (or think you've correctly decrypted!) its ciphertext.

## Test data fields
ciphertext_id - A unique ID for each line's ciphertext in the set.
ciphertext - A segment of encrypted text.
difficulty - Each document has been encrypted with between 1 and 4 ciphers. The difficulty level of a segment of ciphertext denotes which ciphers were used, and in what order (see How has the text been encrypted? above).
