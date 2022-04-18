# Useful String Methods
Let's start thinking about what useful operations we can do on strings with built-in methods, such as finding the length of a text string, joining and splitting strings, substituting one character in a string for another, and more.

## Strings as objects

Most things are objects in JavaScript. When you create a string, for example by using

```
const string = 'This is my string';
```

your variable becomes a string object instance, and as a result has a large number of properties and methods available to it. 

Now, before your brain starts melting, don't worry! You really don't need to know about most of these early on in your learning journey. But there are a few that you'll potentially use quite often we'll look at here.

Let's enter some examples into the browser developer console.

**Finding the length of a string**

Use the length property. Try entering the following lines:

```
const browserType = 'mozilla';
browserType.length;
```

  - This should return the number 7, because "mozilla" is 7 characters long. 

    - This is useful for many reasons; for example, you might want to find the lengths of a series of names so you can display them in order of length, or let a user know a username theyentered into a form field is too long if it is over a certain length.


**Retrieving a specific string character***

You can return any character inside a string by using square bracket notation; this means you include square brackets (```[]```) on the end of your variable name. Inside the square brackets you include the number of the character you want to return, so for example to retrieve the first letter you'd do this:

```
browserType[0];
```

Remember: computers count from 0, not 1!

To retrieve the last character of any string, we could use the following line, combining this technique with the length property we looked at above:

```
browserType[browserType.length-1];
```

The length of the string "mozilla" is 7, but because the count starts at 0, the last character's position is 6; using length-1 gets us the last character.

**Testing if a string contains a substring**

Sometimes you'll want to find if a smaller string is present inside a larger one (we generally say if a substring is present inside a string). This can be done using the ```includes()``` method, which takes a single parameter — the substring you want to search for.

It returns true if the string contains the substring, and false otherwise.

```
const browserType = 'mozilla';

if (browserType.includes('zilla')) {
  console.log('Found zilla!');
} else {
  console.log('No zilla here!');
}
```

Often you'll want to know if a string starts or ends with a particular substring. This is a common enough need that there are two special methods for this: ```startsWith()``` and ```endsWith()```:

```
const browserType = 'mozilla';

if (browserType.startsWith('zilla')) {
  console.log('Found zilla!');
} else {
  console.log('No zilla here!');
}
```

```
const browserType = 'mozilla';

if (browserType.endsWith('zilla')) {
  console.log('Found zilla!');
} else {
  console.log('No zilla here!');
}
```

** Changing case**

The string methods ```toLowerCase()``` and ```toUpperCase()``` take a string and convert all the characters to lower or uppercase, respectively. This can be useful for example if you want to normalize all user-entered data before storing it in a database.

Let's try entering the following lines to see what happens:

```
const radData = 'My NaMe Is MuD';
console.log(radData.toLowerCase());
console.log(radData.toUpperCase());
```

** Updating parts of a string**

You can replace one substring inside a string with another substring using the ```replace()``` method.

In this example, we're providing two parameters; the string we want to replace, and the string we want to replace it with:

```
const browserType = 'mozilla';
const updated = browserType.replace('moz','van');

console.log(updated);      // "vanilla"
console.log(browserType);  // "mozilla"
```

Note that ```replace()```, like many string methods, doesn't change the string it was called on, but returns a new string. 
  - If you want to update the original browserType variable, you would have to do something like this:

```
let browserType = 'mozilla';
browserType = browserType.replace('moz','van');

console.log(browserType);  // "vanilla"
```

Also note we now have to declare ```browswrType``` using ```let```, not ```const```, because we are reassigning it.

Be aware that ```replace()``` in this form only changes the first occurrence of the substring. If you want to change all occurrences, you can use ```replaceAll()```:

```
let quote = 'To be or not to be';
quote = quote.replaceAll('be','code');

console.log(quote);  // "To code or not to code"
```

## Active learning examples

Now try your hand at writing some string manipulation code. 

  - In each exercise below, we have an array of strings, and a loop which processes each value in the array and displays it in a bulleted list. 
  - You don't need to understand arrays or loops right now; these will be explained in future articles. 
  - All you need to do in each case is write the code which will output the strings in the format we want them in.

Each example comes with a "**Show solution**" button you can press to see a potential answer if you get really stuck.


## Filtering greeting messages

In the first exercise we'll start you off simple; we have an array of greeting card messages, but we want to sort them to list just the Christmas messages. We want you to fill in a conditional test inside the ```if( ... ```) structure, to test each string and only print it in the list if it is a Christmas message.

Think about how you could test whether the message in each case is a Christmas message. 
  - What string is present in all of those messages, and what method could you use to test whether it is present?

** Live output**
Happy Birthday!
Merry Christmas my love
A happy Christmas to all the family
You're all I want for Christmas
Get well soon

```
const list = document.querySelector('.output ul');
list.innerHTML = '';
const greetings = ['Happy Birthday!',
                 'Merry Christmas my love',
                 'A happy Christmas to all the family',
                 'You\'re all I want for Christmas',
                 'Get well soon'];

for (let greeting of greetings) {
  // Your conditional test needs to go inside the parentheses
  // in the line below, replacing what's currently there
  if (greeting) {
    const listItem = document.createElement('li');
    listItem.textContent = greeting;
    list.appendChild(listItem);
  }
}
```
SHOW SOLUTION


## Fixing capitalization

In this exercise we have the names of cities in the United Kingdom, but the capitalization is messed up. We want you to change them so they are all lower case, except for a capital first letter. A good way to do this is to:

  - Convert the whole of the string contained in the city variable to lower case and store it in a new variable.
  - Grab the first letter of the string in this new variable and store it in another variable.
  - Using this latest variable as a substring, replace the first letter of the lowercase string with the first letter of the lowercase string changed to upper case. 
  - Store the result of this replace procedure in another new variable.
  - Change the value of the result variable to equal to the final result, not the city.

**Live output**
lonDon
ManCHESTer
BiRmiNGHAM
liVERpoOL

```
const list = document.querySelector('.output ul');
list.innerHTML = '';
const cities = ['lonDon', 'ManCHESTer', 'BiRmiNGHAM', 'liVERpoOL'];

for (let city of cities) {
  // write your code just below here

  const result = city;
  const listItem = document.createElement('li');
  listItem.textContent = result;
  list.appendChild(listItem);
}

```
SHOW SOLUTION

## Making new strings from old parts

In this last exercise, the array contains a bunch of strings containing information about train stations in the North of England. The strings are data items which contain the three-letter station code, followed by some machine-readable data, followed by a semicolon, followed by the human-readable station name. For example:

```
MAN675847583748sjt567654;Manchester Piccadilly
```

We want to extract the station code and name, and put them together in a string with the following structure:

```
MAN: Manchester Piccadilly
```

We'd recommend doing it like this:

  1. Extract the three-letter station code and store it in a new variable.
  2. Find the character index number of the semicolon.
  3. Extract the human-readable station name using the semicolon character index number as a reference point, and store it in a new variable.
  4. Concatenate the two new variables and a string literal to make the final string.
  5. Change the value of the result variable to equal to the final string, not the station.


<details>
  <summary>Click to Show Solution!</summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets
</details>

Thanks! You are awesome!!
Dr. Vicki
