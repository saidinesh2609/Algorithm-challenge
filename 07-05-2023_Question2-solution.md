runners = [
    {'name': 'John', 'speed': 10, 'run_time': 6, 'rest_time': 20},
    {'name': 'James', 'speed': 8, 'run_time': 8, 'rest_time': 25},
    {'name': 'Jenna', 'speed': 12, 'run_time': 5, 'rest_time': 16},
    {'name': 'Josh', 'speed': 7, 'run_time': 7, 'rest_time': 23},
    {'name': 'Jacob', 'speed': 9, 'run_time': 4, 'rest_time': 32},
    {'name': 'Jerry', 'speed': 5, 'run_time': 9, 'rest_time': 18}
]

def calculate_distance(runner, time):
    cycle_time = runner['run_time'] + runner['rest_time']
    full_cycles = time // cycle_time
    remaining_time = time % cycle_time
    distance = full_cycles * runner['run_time'] * runner['speed']
    if remaining_time >= runner['run_time']:
        distance += runner['run_time'] * runner['speed']
    else:
        distance += remaining_time * runner['speed']
    return distance

winning_distance = 0

for runner in runners:
    distance = calculate_distance(runner, 1234)
    if distance > winning_distance:
        winning_distance = distance

print("The distance of the winning runner after 1234 seconds:", winning_distance, "m")
