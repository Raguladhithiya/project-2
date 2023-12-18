#include <stdio.h>

char board[8][8];

void initializeBoard() {
    // Initialize the chessboard with pieces
    char pieces[] = "RNBQKBNR";
    for (int i = 0; i < 8; ++i) {
        board[0][i] = pieces[i];
        board[1][i] = 'P';
        board[6][i] = 'p';
        board[7][i] = pieces[i] + 32; // Lowercase for black pieces
        for (int j = 2; j < 6; ++j) {
            board[j][i] = ' ';
        }
    }
}

void displayBoard() {
    // Display the chessboard
    for (int i = 0; i < 8; ++i) {
        for (int j = 0; j < 8; ++j) {
            printf("%c ", board[i][j]);
        }
        printf("\n");
    }
}

int isValidMove(int startRow, int startCol, int endRow, int endCol) {
    // Add move validation logic here
    // For simplicity, this example allows any move
    return 1;
}

void movePiece(int startRow, int startCol, int endRow, int endCol) {
    // Move the piece on the board
    board[endRow][endCol] = board[startRow][startCol];
    board[startRow][startCol] = ' ';
}

int main() {
    initializeBoard();

    while (1) {
        displayBoard();

        int startRow, startCol, endRow, endCol;

        // Get user input for the move
        printf("Enter start position (row col): ");
        scanf("%d %d", &startRow, &startCol);

        printf("Enter end position (row col): ");
        scanf("%d %d", &endRow, &endCol);

        // Check if the move is valid
        if (isValidMove(startRow, startCol, endRow, endCol)) {
            movePiece(startRow, startCol, endRow, endCol);
        } else {
            printf("Invalid move. Try again.\n");
        }
    }

    return 0;
}
