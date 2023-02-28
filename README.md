# Sed Tutorial


## 1) Replace a word from a file

In file named <strong>file_name</strong>, replace word <strong>word_to_replace</strong> with <strong>new_word</strong>:

```bash
sed 's/word_to_replace/new_word/' file_name
```
<em><strong>Note 1:</strong></em>  <em>This does not directly edit the file</em>

<em><strong>Note 2:</strong></em>  <em>By default, it makes 1 replacement per line to the 1st instance of <strong>word_to_replace</strong></em> 

This is equivalent to:

```bash
sed 's/word_to_replace/new_word/1' file_name
```

Now, replace 2nd instance of <strong>word_to_replace</strong> with <strong>new_word</strong>:

```bash
sed 's/word_to_replace/new_word/2' file_name
```

Finally, replace all instances:

```bash
sed 's/word_to_replace/new_word/g' file_name
```

## 2) Output to a new file and directly to file

- Output to a new file aclled <strong>new_file</strong>

```bash
sed 's/word_to_replace/new_word/g' file_name > new_file
```

- Edit directly to <strong>file_name</strong> (edited inline)

```bash
sed -i 's/word_to_replace/new_word/g' file_name
```

## 3) Handle forward slashes

```bash
sed -i 's/word1_separated_by_slash\/word1\//new_word2\/word2\//' file_name
```
Here we are escaping forward slashes, as we can see this is not very optimal.

We can user another character as long as it is in the correct format:

```bash
sed -i 's!word1_separated_by_slash/word1/!new_word2/word2/!' file_name
```

With this, we can now use forward slashes. This is a better version.

## 4) Insert a new line

Insert a new line at line 3, with the contents: <strong>New line with sed</strong>

```bash
sed -i '3 i New line with sed' file_name
```

## 5) Replace a line

Replace line starting with <strong>hello</strong> with new line containing: <strong>hello_updated</strong>:

```bash
sed -i 's/^hello.*/hello_updated/' file_name
```

Replace line starting with <strong>hello</strong> with 2 new lines using <strong>\n</strong> to jump to the next line: 

```bash
sed -i 's/^hello.*/line_1\nline_2/' file_name
```
This will replace all lines starting with <strong>hello</strong> with:

<strong>line_1</strong>

<strong>line_2</strong>