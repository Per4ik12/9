# 9

# Ввод максимальной массы, которую может выдержать лодка
max_weight = int(input("Введите максимальную массу, которую может выдержать лодка: "))
while max_weight < 1 or max_weight > 10**6:
    print("Некорректный ввод. Максимальная масса должна быть в диапазоне от 1 до 10^6.")
    max_weight = int(input("Введите максимальную массу, которую может выдержать лодка: "))

# Ввод количества рыбаков
num_fishermen = int(input("Введите количество рыбаков: "))
while num_fishermen < 1 or num_fishermen > 100:
    print("Некорректный ввод. Количество рыбаков должно быть в диапазоне от 1 до 100.")
    num_fishermen = int(input("Введите количество рыбаков: "))

# Ввод веса каждого рыбака
weights = []
for i in range(num_fishermen):
    weight = int(input(f"Введите вес рыбака {i+1}: "))
    while weight < 1 or weight > max_weight:
        print(f"Некорректный ввод. Вес рыбака должен быть в диапазоне от 1 до {max_weight}.")
        weight = int(input(f"Введите вес рыбака {i+1}: "))
    weights.append(weight)

# Функция для вычисления минимального количества лодок
def min_boats(weights, max_weight):
    weights.sort(reverse=True)  # Сортируем веса по убыванию
    boats = 0
    curr_weight = 0
    
    for weight in weights:
        if curr_weight + weight <= max_weight:
            curr_weight += weight
        else:
            boats += 1
            curr_weight = weight
    
    return boats + 1 if curr_weight > 0 else boats

# Вывод результата
min_num_boats = min_boats(weights, max_weight)
print(f"Минимальное количество лодок: {min_num_boats}")
