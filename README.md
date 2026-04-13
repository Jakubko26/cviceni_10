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
data = read_data("data.json", "unordered_numbers")
    sorted_data = read_data("data.json", "ordered_numbers")
    dna = read_data("data.json", "dna_sequence")

    sizes = [100, 500, 1000, 5000, 10000]

    linear_times = []
    binary_times = []
    set_times = []

    for n in sizes:
        # simulujeme rôzne veľkosti zo vstupu JSON
        sample = data[:min(n, len(data))]
        sorted_sample = sorted_data[:min(n, len(sorted_data))]

        target = sample[len(sample) // 2]
        s = set(sample)

        linear_times.append(measure(linear_search, sample, target))
        binary_times.append(measure(binary_search, sorted_sample, target))
        set_times.append(measure(set_search, s, target))

        print(f"Hotovo n = {n}")

    # -------------------------
    # GRAF
    # -------------------------

    plt.plot(sizes, linear_times, label="Linear search")
    plt.plot(sizes, binary_times, label="Binary search")
    plt.plot(sizes, set_times, label="Set search")

    plt.xlabel("Veľkosť vstupu")
    plt.ylabel("Čas (sekundy)")
    plt.title("Porovnanie algoritmov vyhľadávania")
    plt.legend()

    plt.show(
