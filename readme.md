# CONFOUR

Confour is a robot that plays the game connect four ([Connect Four Wikipedia Page](https://en.wikipedia.org/wiki/Connect_Four)) against human opponents. It was developed as a term project for the EEE212 microprocessors course at Bilkent University. The main requirement of the projects was to use an 8051 microcontroller and the software of Confour runs entirely on an AT89S52 chip. At the end of the term, Confour was one of the four projects that received a best project award.

Here is a YouTube video demonstrating the project:

[![YouTube Video](https://img.youtube.com/vi/5pP6cDErGjs/0.jpg)](https://www.youtube.com/watch?v=5pP6cDErGjs)

## Hardware

Move detection is performed by pairs of IR LEDs and TSOPs for each one of the seven columns. The LEDs are driven by a constantly-on carrier signal simply generated using a 555 timer IC. The TSOPs are able to detect this signal until a dropping piece cuts the line of sight between two matching units.

Confour plays its moves using two servo motors. The first servo pushes one of the Confour's pieces that are stacked on top of each other to a slanted rail. The dropped piece rolls on top of this rail and drops to the column at the end of the rail. There is a total of seven rails, each with a different length corresponding to the seven columns of the board, that are connected side by side on a circular platform. The second servo is able to determine which rail the piece will follow by rotating this platform.

## Software

After detecting a move, Confour calculates a counter move using the Negamax algorithm ([Negamax Wikipedia Page](https://en.wikipedia.org/wiki/Negamax)), which is implemented with the assembly language of the 8051 architecture. Although there are computer programs that are able to solve connect four completely, the microcontroller used in the project is not able to do this due to its limited speed. Instead, it uses an evaluation function, which calculates a score that is roughly an indication of the probability for each player to win for a given board state.

To play even faster, Confour uses an opening book at the start of each game. This opening book consists of previously calculated results for every single board state that might occur during the first eight moves of the game. Confour is able to play its first four moves instantly and perfectly by simply looking them up from this opening book.
