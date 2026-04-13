from pathlib import Path
import json


# -------------------------
# ČÍTANIE JSON DÁT
# -------------------------

def read_data(file_name, field):
    """
    Reads a JSON file and returns data for a given field.
    """
    file_path = Path.cwd() / file_name

    if not file_path.exists():
        return None

    with open(file_path, "r", encoding="utf-8") as f:
        data = json.load(f)

    return data.get(field, None)


# -------------------------
# TEST
# -------------------------

def main():
    unordered = read_data("data.json", "unordered_numbers")
    ordered = read_data("data.json", "ordered_numbers")
    dna = read_data("data.json", "dna_sequence")

    print("Unordered numbers:", unordered[:10] if unordered else None)
    print("Ordered numbers:", ordered[:10] if ordered else None)
    print("DNA:", dna[:50] if dna else None)


if __name__ == "__main__":
    main()
def main():
    nums = unordered_sequence(20)
    sorted_nums = ordered_sequence(20)
    dna = dna_sequence(100)

    print("Unsorted:", nums)
    print("Sorted:", sorted_nums)
    print("DNA:", dna)

    print("\nLinear search:", linear_search(nums, nums[3]))
    print("Binary search:", binary_search(sorted_nums, sorted_nums[5]))
    print("Pattern search:", pattern_search(dna, dna[10:15]))


if __name__ == "__main__":
    main()
