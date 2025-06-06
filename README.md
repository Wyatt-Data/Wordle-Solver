# Wordle Solver 🎯

This project began as a personal challenge to sharpen my R skills after finishing undergrad at **BYU-Idaho** and before starting grad school at **Utah State University**. I wanted to beat my parents at Wordle using statistics—and ended up with my first real foray into **Natural Language Processing (NLP)**.

---

## 🔍 Motivation

My family loves playing Wordle. They kept solving it faster than I could, which led me to ask: _Can I use data to guess smarter?_ I realized:

- Certain letters are more likely in specific positions  
- The first guess drastically reduces the solution space  
- A frequency-based approach could optimize guesses  

This started with a `.txt` file of valid Wordle words and turned into a full R-based analysis with visualizations and basic heuristics.

> _Note: This project was built before I knew anything about ChatGPT or LLMs. Just pure stats, trial and error._

---

## 📦 Included Files

- `Wordle.Rmd`: R Markdown file containing all code and comments  
- `wordle_solver.html`: Knitted output with charts, letter placement, and probability visualizations  
- `wordle-La.txt`: Word list accepted by Wordle (sourced online)  

---

## 🚀 How to Run

1. Clone the repo or download the files  
2. Open `wordle_solver.Rmd` in **RStudio**  
3. Update file paths if necessary  
4. Run all code chunks to load the functions and data

---

## 🧠 How to Play

The game runs using functions defined earlier in the notebook. The code block below is the **core logic**—it's all you need to interact with the solver.

### Feedback Encoding

Use the following numeric codes to represent Wordle’s feedback:

- `0` = Gray (letter not in the word)  
- `1` = Yellow (letter in the word but wrong position)  
- `2` = Green (letter in the correct position)

### Instructions

- For your **first guess**, leave `guess` and `correct` empty. The solver will suggest an opening word.
- After each guess in Wordle:
  - Update `guess` with the word you entered  
  - Update `correct` with a string representing feedback (e.g., `"01020"`)  
- Rerun only this cell to get the next best guess
- To **restart from scratch**, run the initialization cell below this code block to reset the word list

> ⚠️ **Note**: This solver performs poorly on words with **double letters**.  
> There’s a trick to handle those—I'll update this when I remember it.

<details>
<summary>🔧 Core Solver Code</summary>

```r
## PLAY THE GAME HERE ####

# Example input
guess <- "curly"
correct <- "02022"

# Update possible words
dictionary <- creating_dictionary(guess, correct)
remaining_words <- remaining(remaining_words, dictionary)

# Display top suggestions
as.data.frame(
  remaining_words %>%
    arrange(-total_propability) %>%
    head(3) %>%
    select(original_word)
) %>% pander()
```

---

## 🧠 Why It Matters

This was my **first hands-on NLP project**. It helped me:
- Practice writing R functions from scratch
- Manipulate character-level text data
- Gain confidence working with unstructured inputs

It also sparked a broader interest in NLP, which I later pursued in graduate school and beyond.


## 👤 Author

**Wyatt W.**  
Master of Data Analytics – Utah State University  
R enthusiast, Wordle underdog-turned-contender

---
