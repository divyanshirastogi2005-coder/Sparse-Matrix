# Sparse-Matrix
Write a Python program to represent a standard 2D matrix as a Sparse Matrix using a dictionary (which acts like a key-value 3-column triplet representation). Then, find the memory address of an element assuming Row-Major Order storage.
# 1. Sparse Matrix representation using Python dictionary
# Only store non-zero elements: {(row, col): value}
sparse_matrix = {
    (0, 2): 5,
    (1, 0): 12,
    (2, 3): 7
}

# 2. Row-Major Order Address Calculation Function
def calculate_rmo_address(base_address, element_size, total_cols, target_row, target_col):
    """
    Formula: Address = Base_Address + Element_Size * (Target_Row * Total_Cols + Target_Col)
    (Assuming 0-based indexing)
    """
    offset = (target_row * total_cols) + target_col
    address = base_address + (element_size * offset)
    return address

# Example Simulation matching past exam values
BA = 2000          # Base Address
W = 4              # 4 bytes per integer
C = 10             # 10 columns in total matrix
i, j = 2, 3        # Target position

print(f"Value at (2,3): {sparse_matrix.get((i, j), 0)}")
print(f"Physical Memory Address of element (2,3): {calculate_rmo_address(BA, W, C, i, j)}")
