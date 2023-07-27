---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 6&7"
date: 2023-07-25
descripton: "Day 6&7 in AI+웹개발 취업캠프"
tags:
    - diary
---


## 주제. JavaScript 또는 TypeScript 학습, Node.js 실습


##  I. 오목게임
	1. Nodejs와 함께 콘솔창에서 실행되도록 사용자 입출력 도구를 사용한다.  
	2. 오목판 사이즈는 30x30으로 고정한 후 정사각형의 형태의 오목판을 만든다.  
	3. 사용자 입력 도구에 좌표값 (15,15)라고 입력하여 바둑돌을 둔다.  
	4. 흑은 1로, 백은 0으로 표기하여 화면에 흑과 백이  
	번갈아가면서 두도록 입력 도구가 계속 뜨도록 입력 받는다.  
	5. 오목 규칙에 따라 5줄이 먼저 완성되면 “Game over”와 같이 누가 이겼는지 승패를 알리는 출력을 만든다.  
	6. 승패가 계속 나지 않을 경우 실행 후 5분이 지나면 자동 종료시킨다.  
	** 제출 방법 : 작성된 js 파일과 추가된 js 파일 그리고 설치된 module을 메모장에 남겨 제출한다.


### Prerequisites
---
#### Install typescript via npm
![](/posts/posts_images/aiweb_day6_7/install1.png)
https://www.typescriptlang.org/download
https://nodejs.dev/en/learn/nodejs-with-typescript/

This installs `tsc` or TypeScript compiler.


#### Install type definitions for node
![](/posts/posts_images/aiweb_day6_7/install2.png)

```
ReferenceError: prompt is not defined
    at Object.<anonymous> (C:\Users\Eunice\OneDrive - Sogang\바탕 화면\git\ai_webdev\js\main.ts:1:13)
    at Module._compile (node:internal/modules/cjs/loader:1254:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1308:10)
    at Module.load (node:internal/modules/cjs/loader:1117:32)
    at Module._load (node:internal/modules/cjs/loader:958:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
    at node:internal/main/run_main_module:23:47

Node.js v18.15.0
```

### Step 1. 콘솔창에서 사용자 입출력 기능 추가
---
#### prompt() 사용 시 - Install prompt library
![](/posts/posts_images/aiweb_day6_7/install3.png)

```ts
var input = prompt('Write something here: ')
console.log(input)
```

#### readline 사용 시 - Import readline module
https://nodejs.org/api/readline.html

```ts
const readline = require('readline').createInterface({
	input: process.stdin,
	output: process.stdout
});

readline.question("Write something here: ", (answer) => {
	console.log('Your input is \'' + answer + '\'')
});

// OUTPUT
// Write something here: Hello
// Your input is 'Hello'
```


#### receive row and column size as input, try tsc

![](/posts/posts_images/aiweb_day6_7/setup1.png)

NOTE. Running TypeScript file using `Node.JS`

![](/posts/posts_images/aiweb_day6_7/setup2.png)

Although results are the same and it shows that the code runs properly, this does not mean that Node.JS can read TypeScript files. Node.JS reads the TypeScript file, finds whatever is written or works equivalently in JavaScript, and then runs only the JS portion of the code. 

`Node does not execute TypeScript`

CONCLUSION

Compile TypeScript files via `tsc` (tsc compiles `.ts` file to `.js` file, and generates JSON files that contain package data)

```
tsc main.ts
```

![](/posts/posts_images/aiweb_day6_7/setup3.png)

Run compiled JavaScript file via `node`

```
node main.js
```



### Step 2. 오목판 만들기
---

Declare board variable as two-dimensional array
ref. https://www.tutorialspoint.com/typescript/typescript_multi_dimensional_arrays.htm

```ts
const board: string[][] = [];
```

Initialize 30x30 board and fill with '-'.

```ts
for (let i=0; i < 30; i++) {
	const row: string[] = [];
	// traverse columns
	for (let j=0; j < 30; j++) {
		row.push('-');
	}
	board.push(row);
}
```

Create function that prints out board as output

```ts
function output(board: string[][]) {
	for (const row of board) {
		console.log(row.join(' '));
	}
}
output(board);
```


### Step 3&4. (x, y) 사용자 입력받기, 입력에 따라 바둑돌 두기

Receive input via readline in the format of "row column". Once string input is received, split via `String split()` method.

```
string.split([separator][, limit]);
```

More info on `String split()` - https://www.tutorialspoint.com/typescript/typescript_string_split.htm

```ts
// import readline module
const readline = require('readline').createInterface({
	input: process.stdin,
	output: process.stdout
});
```

```ts
// receive user input
readline.question("Input row and column (format: x y) ", (input) => {
	// split input to row, column
	var splitted = input.split(" ", 2);
	// type cast string to number
	row = parseInt(splitted[0]);
	col = parseInt(splitted[1]);
	console.log("Your input is (" + row + ", " + col + ")");
});
```
<br>
Better Implementation. Use `Array map()` method. (Similar logic and usage compared to Python `map()` function).

```
array.map(callback[, thisObject])
```

Receive input via readline, then split via `String split()`, 

```ts
const [row, col] = input.split(' ').map((coord) => parseInt(coord));
```

More info on `Array map()`  - https://www.geeksforgeeks.org/typescript-array-map-method/

#### ISSUE. Continuously receiving input

I initially tried using for and while loops but had trouble laying out the logic with count indicators and making safe code... (Many errors were generated, my life essence was slowly being depleted...)

After some research and looking back at a previous project where I used some JavaScript, I found that using `async/await` was similar in TypeScript and a lot more reliable.

I created an `async` function for getting player input.

```ts
async function getPlayerInput(player: number) {
	// import readline module
	const rl = require('readline').createInterface ({
		input: process.stdin,
		output: process.stdout
	});

	// read and return user input
	return new Promise<string>((resolve) => {
		rl.question(`Player ${player}'s turn (row col): `, (response) => {
			rl.close();
			resolve(response);
		});
	});
}
```

I found out that `readline.question` continuously receives input and does not end (for context, I initially thought this was due to my poor logic in my previouos for and while loops I created -- I now know why Node.js doesn't end when I was testing readline for user input). So I used `readline.close()` to indicate an end to `readline.question()` before calling on to print the board results.

I also found out about the `Promise` function and its usage with `async/await`

More info on `Promise` 
- https://www.educba.com/typescript-promise/
- https://velog.io/@skulter/TypeScript-7.-Promise%EC%99%80-asyncawait-%EA%B5%AC%EB%AC%B8

But basically, I implemented a return process wherein I call the `resolve` function in `Promise` and it checks for user response / input. All of this lead to this portion of the code:

```ts
return new Promise<string>((resolve) => {
	rl.question(`Player ${player}'s turn (row col): `, (response) => {
		rl.close();
		resolve(response);
	});
});
```

#### Updating the board

Minor Changes :
- `흑: 1`, `백: 0` 표시하다가 계속 헷갈려서 흑을 'B' (Black)으로 백을 'W' (White)로 표시하기로 했다.

I made a separate function to apply user input and update the board. I replaced the value of the element in teh board array by using the (row, column) from the user input as indices (x, y). 

```ts
function update(row: number, col: number, player: number) {
	if(board[row][col] === '-') {
		board[row][col] = player === 1 ? 'B' : 'W';
		return true;
	}
	return false;
}
```


#### ISSUE. Continuously running the game

By now, the program infinitely asks for user input and prints the board with updates. But the game has to end (obviously) ... 

I needed to make the program continuously get user input while it checks if a player wins and then force the game to end.

I don't play 오목, I only know that there are black and white players ... So after some research and a helpful English blog, I found out that players need to get 5 of their own pieces in a straight line (whether it be horizontally as a row, vertically as a column, or in a diagonal).

Hence, I applied the following logic as a win condition:

```
Check if any row, column, diagonal has five matching symbols
```


#### Checking Win Condition

Whenever there are five consecutive matching symbols, the function will return `true`. If not, the function will continue to return `false`.

For checking the rows, I implemented a for loop to traverse each element in each row. I used counters to count how many consecutive pieces there were (B or W).

```ts
// check rows
for (let i = 0; i < 30; i++) {
	let countB = 0;
	let countW = 0;
	for (let j = 0; j < 30; j++) {
		if (board[i][j] === 'B') {
			countB++;
			countW = 0;
		} else if (board[i][j] === 'W') {
			countW++;
			countB = 0;
		} else {
			countB = 0;
			countW = 0;
		}
		if (countB === 5 || countW === 5) {
			return true;
		}
	}
}
```

For checking the columns, I used a for loop to traverse each element in the same y axis (since elements on the same columns have the same y coordinates).

```ts
// check columns
for (let j = 0; j < 30; j++) {
	let countB = 0;
	let countW = 0;
	for (let i = 0; i < 30; i++) {
		if (board[i][j] === 'B') {
			countB++;
			countW = 0;
		} else if (board[i][j] === 'W') {
			countW++;
			countB = 0;
		} else {
			countB = 0;
			countW = 0;
		}

		if (countB === 5 || countW === 5) {
			return true;
		}
	}
}
```

Diagonals are always a bit tricky. But I looked at my old C code for building a Tetris game. So while reminiscing the old days and after doing a few tests and some trial and error,  I managed to make the following function. The logic is a merge of traversing both the rows and columns while counting the consecutive matching pieces via an additional index k.

```ts
// check diagonals
for (let i = 0; i < 30; i++) {
    for (let j = 0; j < 30; j++) {
        // check diagonals
        // start from (i, j) going right and down
        let countB = 0;
        let countW = 0;
        for (let k = 0; k < 5; k++) {
            if (i + k < 30 && j + k < 30) {
                if (board[i + k][j + k] === 'B') {
                    countB++;
                    countW = 0;
                } else if (board[i + k][j + k] === 'W') {
                    countW++;
                    countB = 0;
                } else {
                    countB = 0;
                    countW = 0;
                }

                if (countB === 5 || countW === 5) {
                    return true;
                }
            }
        }

        // Check diagonals starting from position (i, j) going right and up
        countB = 0;
        countW = 0;
        for (let k = 0; k < 5; k++) {
            if (i - k >= 0 && j + k < 30) {
                if (board[i - k][j + k] === 'B') {
                    countB++;
                    countW = 0;
                } else if (board[i - k][j + k] === 'W') {
                    countW++;
                    countB = 0;
                } else {
                    countB = 0;
                    countW = 0;
                }

                if (countB === 5 || countW === 5) {
                    return true;
                }
            }
        }
    }
}

```



## Step 5. 게임 결과 ( Finally . . . )

Simple `Game Over` message

```ts
console.log(`GAME OVER. Player ${currentPlayer === 1 ? '1' : '2'} wins!`);
```

BEST CASE. 
계속 한 방향에 바둑돌을 두는 사례 (Player 1 하고 Player 2 각자 멍청할 경우)
<br>
![](/posts/posts_images/aiweb_day6_7/board_output.png)

Player Input 순서

```
P1 15 15
P2 16 16
P1 16 15
P2 17 16
P1 17 15
P2 18 16
P1 18 15
P2 19 16
P1 19 15
```

<br><br><br>

## II. null vs. undefined
	1. 어떨때 값이 null이 되고 undefined으로 저장되는지 가능한 모든 케이스의 js 코드를 작성한다.
	2. 각 케이스의 코드상에 저장된 변수가 왜 null이고 undefined인지 원인을 설명한다.
	3. 비교연산자를 활용하여 각각의 케이스에 따라 null인지 undefined인지 확인하는 코드를 작성한다.  
	** 제출 방법 : 작성된 js 파일과 내용을 설명할 수 있는 텍스트를 주석을 활용하여 기입한다.


### 간단한 설명
undefined하고 null은 둘 다 정의된 값이 없음을 나타낸다.
- undefined는 변수가 선언되었지만 값이 없음을 나타내요 
  (변수 이름만 정했고 아직 값이 없음, "will 또는 supposed to have a value")
- null은 아예 값이 없음을 나타내요 
  (변수가 값을 가지고 있지 않음, empty 또는 "no value"랑 비슷함)

<참고>[https://2ssue.github.io/common_questions_for_Web_Developer/docs/Javascript/13_undefined&null.html](https://2ssue.github.io/common_questions_for_Web_Developer/docs/Javascript/13_undefined&null.html) 
[https://helloworldjavascript.net/pages/160-null-undefined.html](https://helloworldjavascript.net/pages/160-null-undefined.html)  
[https://www.scaler.com/topics/javascript/null-and-undefined-in-javascript/](https://www.scaler.com/topics/javascript/null-and-undefined-in-javascript/)



## CONCLUSION

#### TODO
- `<과제 I>` <br>
	`- Add timer and implement condition #6` <br>
	`- HTML and CSS visual UI implementation (Maybe)`
- `<과제 II>` <br>
	`-Create JS file to test null and undefined values`
- `Sleep ...`

#### INSPIRATION
- https://mrkool.tistory.com/51
- https://wooder2050.medium.com/%EB%B0%94%EB%8B%90%EB%9D%BC%EC%BD%94%EB%94%A9-prep-course-11%EC%9D%BC%EC%B0%A8-4ab608a6a67d
- https://www.youtube.com/watch?v=TO6qC0nlwZs

#### SOURCE CODE

https://github.com/ganyunhee/ai_webdev/tree/main/js_ts/omok_game
https://github.com/ganyunhee/ai_webdev/tree/main/js_ts/null_undefined





<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프 