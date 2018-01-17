# Project-03
## Anagram solver

### About the project.

This project is to design an anagram solver, the user will be given an input area, here they can enter up to 3 letters and here they will be able to see a word that matches the most with the letters that they have entered, if they enter special characters or even numbers the acronym will not be shown and a message will print telling them that it is not letters. The purpose of the game is to allow the user to solve acronyms that they need to.

### The Planning.

The first stage to planning the project was creating the user stories, I used them to follow

### This is the code I used

``` cpp
#include <iostream> // allows input and output on a system
#include <fstream> // allows the use of ifstreams
#include <string> // allows the use of strings
#include <cstdlib> // allows many functions such as sorting and random number generation
#include <map> // allows map functons to be used 

using namespace std;

void solution(string a, string w);  // The void solution means that it will have no return within the program
  string answer; // This is the string that keeps the answer and can store the values for it.
  int lastScore; // declares the variable name as lastscore

int main() {
  string filename = "dictionary.txt"; // set the file that is being opened.


      string userin; // userin is the string for the input.
  do { 
    cout << "Enter 3 letters here: ";
    getline(cin, userin); // Getline is where it retrieves the input for userin.
  } while(userin.length() > 3);// loop for entering 3 letters.


   // Read from the file.
   ifstream fin(filename.c_str());  // ifstream is the work on a separate file, filename represents a file that is being opened.
      if (!fin) { // fin is the file that is being opened, the ! can switch a false value to true and a true to false, so its saying fin not being opened as its !fin with the if function.
        cout << "error file not able to retrieve"; // this is the message printed if unable to retrieve the word from the file.
      abort(); // if the file cannot be opened exit the program.
   }
    string line; 
    
    while (fin >> line) {  
    
      if(userin.length() >= line.length()){  // This is the checking the line length.
        solution(userin, line);
      }
    }
    
   fin.close();  // close the file and disconnects it with the program after it is done with it.
   
   cout << "Best Solution: " << answer << endl; // This prints out best solution if 3 letters.
   return 0;
}

void solution(string a, string w){ // Give no return on the two strings
   if (  answer.length() > w.length()) return; // returns the string for the user if the solution is retrieved. 
  int currentScore = 0;  // sets currentScore variable score to 0
  map<char, int> reapeatedChars; // map is what stores the score to the values and can search for them when they are retrieved
  
  for(unsigned i=0; i < a.length(); i++) {  // Score system, each letter has one point
    for(unsigned j=0; j < w.length(); j++) { //  if letter is found in anagram that is in dictionary, gives one point 
    if(a[i] == w[j]){ // if a character [i] = w character [j] 
      reapeatedChars[w[j]]++; 
    if(reapeatedChars[w[j]] == 1){ 
      currentScore++;
        }
      }
    }
  }
  if(currentScore > lastScore){  // currentScore is bigger lastScore, give answer
      answer = w; // answer being known as w
      lastScore = currentScore; // gives the answer.
  }
}

```
### IDE's and implementation.

When I was implementing the code, the main IDE I used was repl.it, I have used this before and it remains to be a very useful IDE, the fast testing and debugging options that it gives greatly improve the time that the project was completed in, because of this I will continue to use Repl.it as my usual IDE unless specified by a project brief. The repl.it IDE allows me to constantly test my program as I am building it, this allows me to look at any bugs that are within my code and debug it at each step instead of having a few to fix at the end of the program.

### Debugging.

As repl.it has many features that help with debugging for example having syntax colouring on the code to also having its own in built debugger. By using the debugger, I was anle to look at specific parts of the code in order to figure out what was wrong with the code. With debugging, the repl.it will show the line of code that it does not understand, I then used that to look back on the variables and processes within the program.
