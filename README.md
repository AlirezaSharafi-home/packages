# sorting packages based on its dimesions (volume) and weight
def sort(inputs: list) -> str:
    # Calculate the volume of the package
    width = inputs[0]
    height = inputs[1]
    length = inputs[2]
    weight = inputs[3]
    volume = width * height * length

    # Determine if the package is bulky
    bulky = volume >= 1000000 or max(width, height, length) >= 150

    # Determine if the package is heavy
    heavy = weight >= 20

    # Determine the stack for the package
    if bulky and heavy:
        return "REJECTED"  # Both bulky and heavy
    elif bulky or heavy:
        return "SPECIAL"   # Either bulky or heavy
    else:
        return "STANDARD"  # Neither bulky nor heavy

if __name__ == "__main__":
    try:
        print(sort([40, 60, 60, 10]))   # Output will be STANDARD
        print(sort([200, 60, 50, 10]))    # Output will be SPECIAL (bulky)
        print(sort([40, 60, 70, 40]))     # Output will be SPECIAL (heavy)
        print(sort([300, 150, 200, 40]))  # Output will be REJECTED (both heavy and bulky
    except Exception as e:
        print(f"Something failed, sorry.: {e}")
