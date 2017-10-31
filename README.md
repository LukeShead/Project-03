# Project-03
Anagram solver


### This is the code I used

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
