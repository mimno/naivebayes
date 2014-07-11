# Exploring classifier "confusion"

This page loads a corpus of labeled documents and trains a multi-label Naive Bayes classifier.
The page then compares each document to each label _as if that document were not part of the training set_ and records the most likely category.
Some documents will be "correctly" classified, but others will match another class.

We view the relationship between human-applied labels and computationally inferred labels with a grid.
As an example, we include a collection of Danish folktales collected by Evald Tang Kristensen (1843-1929) and (translated by Tim Tangherlini)[http://www.amazon.com/Folktales-Legends-Stories-Directions-Scandinavian/dp/029599259X].
Kristensen organized these stories into multiple volumes, which we use as labels.

Each row of the grid represents the stories Kristensen assigned to a label, and each column represents the stories assigned by the classifier to a label.
This is the "confusion matrix" of the classifier, which shows relationships between different labels.
The size of each circle at the intersection of a row and a column represents the number of stories with that classification pattern.
To allow for greater variability in their size, circles are semi-transparent and may overlap.
"Correctly" classified stories are therefore shown on the diagonal, in light blue.
Stories that have greater affinity to other classes are shown in light red.

Sometimes we are interested in a confusion matrix to understand how to fix errors in classification.
Other times we want to understand how the classes relate to each other, and to find stories that appear to cross between classes.
For this corpus, we are interested in the confusion matrix because we *want* to be confused.

Clicking on any of the circles will bring up the actual stories in each classification category, such as "Robbers, murderers and thieves" classified as 
"Revenants and their conjuring".
At the top of the window will be an ordered list of words that are shared by documents in both classes and have significant association (according to Dunning's g2 metric) with one or other class.
Words associated with the "correct" class are on the left; words associated with the inferred class are on the right.
The significance of the association is shown with the text color.

The input format for this system is a three-column spreadsheet in tab-delimited format.
There is one row for each document.
The first column is a document identifier, the second column is the label, and the third contains the full text of the document.
By default, the page loads a document in the current directory called `input.txt`.