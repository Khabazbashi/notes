# regex_tutorial
Learn and practice@[Regex101](https://regex101.com/ "good page for practice")


## Flags
| expression | full | desc |
| :-: | :- | :- |
| g | global | Instructs the engine not to stop after the first match has been found, but rather to continue until no more matches can be found. |
| i | insensitive | A case insensitive match is performed, meaning capital letters will be matched by non-capital letters and vice versa.
| m | multi line | Causes ^ and \$ to match the begin/end of each line (not only begin/end of string).
| s | single line | Enables the dot metacharacter "." to also match newlines. All lines are treated as a single line input. |
| n | no capture | All capturing groups () are instead treated as if they were non-capturing groups (?:). 
| x | extended | Tells the engine to ignore all whitespace and allow for comments in the regex. Comments are indicated by a starting "#"-character. Spaces and text after a # in the pattern are ignored. |
| R | right to left | The .NET regex engine now performs matches from right to left, instead of left ro right.|


## General tokens
| expression | desc 
| -: | - | 
| \n | newline | 
| \r | carriage return | 
| \t | horizontal tab | 
| \v | vertical tab |
| \0 | null character, do not follow with another digit. |
| a\|b | Matches either what is before or after the  \| |


## Character Classes 
| expression | desc | example| note |
| -: | - | - |  - |
| abc | Match any "abc" |
| [a-c] | Match any characters between a-c |
| [^a-c] | Match anything but characters between a-c |
| [abc] | Match any a, b or c |
| [^abc] | Match anything but a, b or c |
| [a-cA-C] | Match any characters between a-c or A-C |
| [^a-cA-C] | Match anything but characters between a-c or A-C |
| [a-c-[b]] | Match any character between a-c, except for any of the characters defined in the nested class |
| . | Matches any single character other than newline (\n, \r, \u2028 or \u2029) | `.y` => m`y`, a`y`| *Does not match yes. Multiline flag doesn't change the dot behavior.  Inside a character class, the dot loses its special meaning.*|
| \s | Matches any kind of space, tab or newline (equivalent to [\f\n\r\t\v])|
| \S+ | Matches anything other than a space, tab or newline |
| \w | Match any word character (letter, digit, underscore equivalent to [a-zA-Z0-9_]) |
| \w+ | Matches all words  | `\w+` => `Hello there my name is` |
| ^\w+ | Matches the first word in a string | `^\w+` => `Hello` there my name is |
| \W+ | Matches anything other than a word (equivalent to [^a-zA-Z0-9_]) |
| \d | Matches any digit (equivalent to [0-9]) |
| \D+ | Matches anything other than a digit |
| [\b] | Matches a backspace  |


## Quantifiers
| expression | desc | example | note
| -: | - | - | - |
| {3} | Matches the previous token exactly 3 consecutive times | `tea{3}` => `teaaa`, `teaaa`aa| *does not match tea, teaa* |
| {3,} | Matches the previous token at least 3 consecutive times | `tea{3,}` => `teaaa` `teaaaaa`time | *does not match tea, teaa*|
| {3, 4} | Matches the previous token between 3 and 4 consecutive times | `tea{3,4}` => `teaaa`, `teaaaa`aaa` | *does not match tea, teaa* |
| ? | Matches the previous token **zero** or **one** time | `tea?` => `te`, `tea`, `tea`aaa | *matches everything if used with a single previous token (a\*) because it also matches zero tokens* |
| * | Matches the previous token **zero** and unlimited times, as many times as possible |  `tea*` => `te`, `tea`, `teaaa`time | *matches everything if used with a single previous token (a\*) because it also matches zero tokens* |
| + | Matches the previous token **one** and unlimited times, as many times as possible | `tea+ => tea, teaa, teaaa`  | *does not match te* | 
|x*? x+? x?? x{n}? x{n,}? x{n,m}? | By default quantifiers like * and + are "greedy", meaning that they try to match as much of the string as possible. The ? character after the quantifier makes the quantifier "non-greedy": meaning that it will stop as soon as it finds a match. |


## Groups and backreferences
| expression | desc | example | note | 
| - | - | - | - | 
|(...)| Capturing group. Matches group and remembers the match. |
| (?:...) | Non-capturing group. Matches group but does not remember the match, cannot be recalled from backreference.
| \n | Backreference (positive integer). Matches the same text as most recently matched by the 1st capturing group. |
| $n | Backreference (positive integer). Inserts the same text as most recently matched by the 1st capturing group. |
| ...(?=...) | Positive Lookahead. Matches the previous token if the given subpattern is matched. Does not consume any characters. | `tea(?=pot)` => `tea`pot| *does not match teacup* |
| ...(?!...) | Negative Lookahead. Matches the previous token if the given subpattern is not matched. Does not consume any characters. | `tea(?!=pot)`=> `tea`cup | *does not match teapot* |
| (?<=...)...|  Positive Lookbehind. Matches the preceeding token if the given subpattern is matched. Does not consume any characters. | `(?<=tea)pot` => tea`pot`| *doest not match coffepot*|
| (?<!...)... | Negative Lookbehind. Matches the preceeding token if the given subpattern is not matched. Does not consume any characters. | `(?<!tea)pot` => coffe`pot`| *does not match teapot* |


## Anchors and boundary-type assertions
| expression | desc | example | note |
| -: | - | - | - |
| ^ | Matches the start of a string | `^t` => `t`ea  | *does not match eat*| 
| $ | Matches the end of a string | `t$` => ea`t`  | *does not match teater*| 
| \b | Matches a word boundary. This is the position where a word character is not followed or preceded by another word-character, such as between a letter and a space.| `/\bm/` => `m`oon `/oon\b/` => m`oon`| *a matched word boundary is not included in the match.* |
| \B | Matches a non-word boundary. This is a position where the previous and next character are of the same type. | `\Bon` => `on`, at no`on`|



## Examples
* ### Match numbers containing floating point
    ```csharp
    @"\d+\.\d+"
    ```
* ### Extract all characters between two strings
    ```csharp
    @"(?<=...)(.*)(?=...)"
    // Will return the outer most match if nested matches in a string
    // Starts over after a newline character
    ```
* ### Match years between 1900 and 1990
    ```csharp
        @"19[0-8]\d"
    ```
* ### Match 24-bit hexadecimal colors
    ```csharp
        @"#(\d|[A-F]){6}"
    ```
* ### Match grayscale colors
    ```csharp
        @"#([0-9a-fA-F]{1,2})\1\1"
    ```
* ### Match lines that are more than 30 characters long
    ```csharp
        @".{30,}"
    ```
* ### Remove repeating words
    ```csharp
        @"\b(.+)\b\s+\1"
        // replace with $1
    ```
* ### Match HTML tags
    ```csharp
        @"<[^<>]+>"
        // <p>testing</p> => <p></p>
    ```
* ### Insert spaces in long numbers for better readability
    ```csharp
        @"(\d)(?=(\d{3})+\b)"
        // 1236800000 => 1 236 800 000
    ```
* ### Round the number to two decimal places
    ```csharp
        @"(?<=\.)(\d{2})\d*"
    ```
* ### Extract query string from URL
    ```csharp
        @"\?.*"
        // https://www.google.com/search?q=regexp => ?q=regexp
    ```
 * ### Match the first character (digit, underscore, letter) in a string
    ```csharp
        @"^\w"
    ```
 * ### Match the first word in a string
    ```csharp
        @"^\w+"
    ```
* ### Match the first word of each line (newline character) in a string
    ```csharp
        @"^\w+", RegexOptions.Multiline
    ```
