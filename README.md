Download Link: https://assignmentchef.com/product/solved-csci2275-assignment-3-word-analysis
<br>
There are several fields in computer science that aim to understand how people use language. This can include analyzing the most frequently used words by certain authors, and then going one step further to ask a question such as: “Given what we know about Hemingway’s language patterns, do we believe Hemingway wrote this lost manuscript?” In this assignment, we’re going to do a basic introduction to document analysis by determining the number of unique words and the most frequently used words in two documents.




Please read all directions for the assignment carefully. This write-up contains both the details of what your program needs to do as well as implementation requirements for how the functionality needs to be implemented.




<h2>What your program needs to do</h2>

There is one test file on Moodle – <em>HungerGames_edit.txt</em>​  ​ that contain the full text from <em>Hunger Games Book 1</em>​ ​. We have pre-processed the file to remove all punctuation and down-cased all words.




Your program needs to read in the .txt file, with the name of the file to open set as a command-line argument. Your program needs to store the unique words found in the file in a dynamically allocated array and calculate and output the following information:

<ul>

 <li>The top <em>n</em>​ ​ words (<em>n</em>​ ​ is also a command-line argument) and the number of times each word was found</li>

 <li>The total number of unique words in the file</li>

 <li>The total number of words in the file</li>

 <li>The number of array doublings needed to store all unique words in the file</li>

 <li>Printout the count of the given words in command line argument</li>

</ul>







<strong>Example: </strong>




Running your program using:




./Assignment3 10 HungerGames_edit.txt ignoreWords.txt

meadow,listen




would return the 10 most common words in the file <em>HungerGames_edit.txt</em>​       ​ and should produce the following results.




682 – is

492 – peeta

479 – its 431 – im

427 – can

414 – says 379 – him

368 – when

367 – no

356 – are

#

Array doubled: 7

#

Unique non-common words: 7682 #

Total non-common words: 59157

# meadow – 12 listen – 23




<strong>Program specifications </strong>

<h2>Use an array of struct to store the words and their counts and a class to store the array and all the functions</h2>

There are specific requirements for how your program needs to be implemented. For this assignment, you need to use a dynamically allocated <strong>array of objects</strong>​           to​        store the words and their counts. Your class needs to have members for the word and count:




struct wordItem

{     string word;     int count;

};

class WordAnalysis

{




// Should store an array of the above struct

// Should store an array of the 50 stop words

// Should also have functions that are given below

}

<strong> </strong>

<h2>Exclude these top 50 common words from your word counting</h2>

Table 1 shows the 50 most common words in the English language. In your code, exclude these words from the words you count in the .txt file. The words are included in a .txt file that you code needs to read in and populate a common word array. Your code should include a separate function, called ​<em>isStopWord()</em>​ to determine if the current word read from the .txt file is on this list and only process the word if it is not.




<strong>Table 1. Top 50 most common words in the English language </strong>

<table width="588">

 <tbody>

  <tr>

   <td width="98">Rank</td>

   <td width="98">Word</td>

   <td width="98">Rank</td>

   <td width="98">Word</td>

   <td width="98">Rank</td>

   <td width="98">Word</td>

  </tr>

  <tr>

   <td width="98">1</td>

   <td width="98">The</td>

   <td width="98">18</td>

   <td width="98">You</td>

   <td width="98">35</td>

   <td width="98">One</td>

  </tr>

  <tr>

   <td width="98">2</td>

   <td width="98">Be</td>

   <td width="98">19</td>

   <td width="98">Do</td>

   <td width="98">36</td>

   <td width="98">All</td>

  </tr>

  <tr>

   <td width="98">3</td>

   <td width="98">To</td>

   <td width="98">20</td>

   <td width="98">At</td>

   <td width="98">37</td>

   <td width="98">Would</td>

  </tr>

  <tr>

   <td width="98">4</td>

   <td width="98">Of</td>

   <td width="98">21</td>

   <td width="98">This</td>

   <td width="98">38</td>

   <td width="98">There</td>

  </tr>

  <tr>

   <td width="98">5</td>

   <td width="98">And</td>

   <td width="98">22</td>

   <td width="98">But</td>

   <td width="98">39</td>

   <td width="98">Their</td>

  </tr>

  <tr>

   <td width="98">6</td>

   <td width="98">A</td>

   <td width="98">23</td>

   <td width="98">His</td>

   <td width="98">40</td>

   <td width="98">What</td>

  </tr>

  <tr>

   <td width="98">7</td>

   <td width="98">In</td>

   <td width="98">24</td>

   <td width="98">By</td>

   <td width="98">41</td>

   <td width="98">So</td>

  </tr>

  <tr>

   <td width="98">8</td>

   <td width="98">That</td>

   <td width="98">25</td>

   <td width="98">From</td>

   <td width="98">42</td>

   <td width="98">Up</td>

  </tr>

  <tr>

   <td width="98">9</td>

   <td width="98">Have</td>

   <td width="98">26</td>

   <td width="98">They</td>

   <td width="98">43</td>

   <td width="98">Out</td>

  </tr>

  <tr>

   <td width="98">10</td>

   <td width="98">I</td>

   <td width="98">27</td>

   <td width="98">We</td>

   <td width="98">44</td>

   <td width="98">If</td>

  </tr>

  <tr>

   <td width="98">11</td>

   <td width="98">It</td>

   <td width="98">28</td>

   <td width="98">Say</td>

   <td width="98">45</td>

   <td width="98">About</td>

  </tr>

  <tr>

   <td width="98">12</td>

   <td width="98">For</td>

   <td width="98">29</td>

   <td width="98">Her</td>

   <td width="98">46</td>

   <td width="98">Who</td>

  </tr>

  <tr>

   <td width="98">13</td>

   <td width="98">Not</td>

   <td width="98">30</td>

   <td width="98">She</td>

   <td width="98">47</td>

   <td width="98">Get</td>

  </tr>

  <tr>

   <td width="98">14</td>

   <td width="98">On</td>

   <td width="98">31</td>

   <td width="98">Or</td>

   <td width="98">48</td>

   <td width="98">Which</td>

  </tr>

  <tr>

   <td width="98">15</td>

   <td width="98">With</td>

   <td width="98">32</td>

   <td width="98">An</td>

   <td width="98">49</td>

   <td width="98">Go</td>

  </tr>

  <tr>

   <td width="98">16</td>

   <td width="98">He</td>

   <td width="98">33</td>

   <td width="98">Will</td>

   <td width="98">50</td>

   <td width="98">Me</td>

  </tr>

  <tr>

   <td width="98">17</td>

   <td width="98">As</td>

   <td width="98">34</td>

   <td width="98">My</td>

   <td width="98"> </td>

   <td width="98"> </td>

  </tr>

 </tbody>

</table>




<h2>Use 4 command-line arguments</h2>

Your program needs to have three command-line arguments – the first argument is the number of most frequent words to output, the second argument is the name of the file to open and read, and the third argument is the name of the file that contains the words to ignore, also called ​<em>stop words</em>​. The 4​<sup>th</sup><sup>​</sup> command line argument will be a list of words separated by commas.




Note: DO NOT HAVE SPACE BETWEEN THE WORDS YOU WANT TO SEARCH

OTHERWISE THEY WILL BE TREATED AS SEPARATE ARGUMENTS




For example, running




./Assignment3 20 HungerGames_edit.txt ignoreWords.txt

meadow,listen




will read the <em>HungerGames_edit.txt</em>​ ​ file and output the ​<em>20</em>​ most frequent words found in the file, not including the words listed in ​<em>ignoreWords.txt </em>​and then search for words meadow and listen.




<strong>Use the array-doubling algorithm to increase the size of your array </strong>We don’t know ahead of time how many unique words either of these files has, so you don’t know how big the array should be. <strong>Start with an array size of 100</strong>​   , and​    double the size as words are read in from the file and the array fills up with new words. Use dynamic memory allocation to create your array, copy the values from the current array into the new array, and then free the memory used for the current array.




Note: some of you might wonder why we’re not using C++ Vectors for this assignment. A vector is an interface to a dynamically allocated array that uses array doubling to increase its size. In this assignment, you’re doing what happens behind-the-scenes with a Vector.




<h2>Output the top <em>n</em>​ ​ most frequent words</h2>

Write a function to determine the top <em>n</em>​ ​ words in the array. This can be a function that sorts the entire array, or a function that generates an array of the <em>n</em>​ ​ top items. Output the <em>n</em>​ ​ most frequent words in the order of most frequent to least frequent.

<strong> </strong>

<h2>Format your output the following way</h2>

When you output the top <em>n</em>​ ​ words in the file, the output needs to be in order, with the most frequent word printed first. The format for the output needs to be:




Count – Word

#

Array doubled: &lt;number of array doublings&gt;

#

Unique non-common words:  &lt;number of unique words&gt;

#

Total non-common words: &lt;total number of words&gt;

#

Search words : count




Generate the output with these commands:




cout&lt;&lt;numCount&lt;&lt;” – “&lt;&lt;word&lt;&lt;endl;

cout&lt;&lt;”#”&lt;&lt;endl;

cout&lt;&lt;”Array doubled: “&lt;&lt;numDoublings&lt;&lt;endl;

cout&lt;&lt;”#”&lt;&lt;endl;

cout&lt;&lt;”Unique non-common words: “&lt;&lt;numUniqueWords&lt;&lt;endl;

cout&lt;&lt;word&lt;&lt;” – ”&lt;&lt;count&lt;&lt;endl;




<strong>Your code needs to have a class that will have the array of struct and also the following methods: </strong>

<strong> </strong>

<strong>/* </strong>

<ul>

 <li><strong>Function name: isStopWord </strong></li>

 <li><strong>Purpose: to see if a word is a stop word </strong></li>

 <li><strong>@param word – a word (which you want to check if it is a stop word) </strong></li>

 <li><strong>@return – true (if word is a stop word), or false (otherwise) </strong></li>

</ul>

<strong>*/</strong>

<strong>bool</strong><strong> isStopWor</strong>​ <strong>d(string word);</strong>​

<strong> </strong>

<strong>/* </strong>

<ul>

 <li><strong>Function name: printTopN </strong></li>

 <li><strong>Purpose: to print the top N high frequency words from a sorted array </strong></li>

 <li><strong>@param topN – the number of top frequency words to print </strong></li>

 <li><strong>@return none </strong></li>

</ul>

<strong>*</strong>​<strong>/ </strong>

<strong>voi</strong>​<strong>d printTo</strong>​<strong>pN(</strong>​<strong> in</strong>​<strong>t topN)</strong>​<strong>; </strong>

<strong> </strong>

<strong>/* </strong>

<ul>

 <li><strong>Function name: </strong>​<strong>searchCount</strong></li>

 <li><strong>Purpose: To search the count of a given word </strong></li>

 <li><strong>@param wordItemList – a pointer that points to a array of wordItems * @param word – the words to search </strong></li>

 <li><strong>@return int – Count of the given word. Will return -1 if not found </strong></li>

</ul>

<strong>*</strong>​<strong>/ </strong>

<strong> </strong>

<strong>int</strong>​<strong> searchCount</strong>​<strong>(</strong>​<strong> string word</strong>​<strong>)</strong>​<strong>; </strong>

<strong> </strong>

<strong>/* </strong>

<ul>

 <li><strong>Function name: </strong>​<strong>addWord</strong></li>

 <li><strong>Purpose: To take in a string and add it to the array of struct. This function should call an internal private function which will handle the array doubling. It should also check if the word exists and only increase the count if it does. The word should be added in a sorted location. </strong></li>

 <li><strong>@param word – the words to search </strong></li>

 <li><strong>@return None </strong></li>

</ul>

<strong>*</strong>​<strong>/ </strong>

<strong> </strong>

<strong>void </strong>​<strong>addWord</strong>​<strong>(</strong>​<strong>string word</strong>​<strong>)</strong>​<strong>; </strong>

<strong> </strong>