# 스도쿠 확인
```Kotlin
class ValidSudoku {
    private fun checkSquareInfo(board: Array<CharArray>, squareStartPoint: Array<Int>): Boolean {
        val squareInfo = BooleanArray(10)

        for (i in squareStartPoint[0] until squareStartPoint[0] + 3) {
            for (j in squareStartPoint[1] until squareStartPoint[1] + 3) {
                if (board[i][j] != '.') {
                    if (squareInfo[board[i][j].digitToInt()]) {
                        return false
                    }

                    squareInfo[board[i][j].digitToInt()] = true
                }
            }
        }

        return true
    }

    private fun checkRowInfo(board: Array<CharArray>, row: Int): Boolean {
        val rowInfo = BooleanArray(10)

        for (i in 0 until 9) {
            if (board[row][i] != '.') {
                if (rowInfo[board[row][i].digitToInt()]) {
                    return false
                }

                rowInfo[board[row][i].digitToInt()] = true
            }
        }

        return true
    }

    private fun checkColumnInfo(board: Array<CharArray>, column: Int): Boolean {
        val columnInfo = BooleanArray(10)

        for (i in 0 until 9) {
            if (board[i][column] != '.') {
                if (columnInfo[board[i][column].digitToInt()]) {
                    return false
                }

                columnInfo[board[i][column].digitToInt()] = true
            }
        }

        return true
    }

    public fun isValidSudoku(board: Array<CharArray>): Boolean {
        var squareStartPoints = arrayOf(
            arrayOf(0, 0),
            arrayOf(0, 3),
            arrayOf(0, 6),
            arrayOf(3, 0),
            arrayOf(3, 3),
            arrayOf(3, 6),
            arrayOf(6, 0),
            arrayOf(6, 3),
            arrayOf(6, 6)
        )

        if (board.isEmpty()) {
            return false
        }

        for (i in 0 until 9) {
            if (!checkRowInfo(board, i)) {
                return false
            }

            if (!checkColumnInfo(board, i)) {
                return false
            }
        }

        for (i in 0 until 9) {
            if (!checkSquareInfo(board, squareStartPoints[i])) {
                return false
            }
        }

        return true
    }
}
```