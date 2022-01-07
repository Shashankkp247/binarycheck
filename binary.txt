# Prompt user for the binary digits
bin = input("Put consecutive number of zeroes and ones to find the longest number of consecutive zeroes : ")

total = 0
for i in bin:
    total += 1

# Check for alphabets
if bin.isalpha() == True:
    print("Error : Put binary digits not alphabets")
    exit(1)

# Check for Speacial chars
ch = "[@_!#$%^&*()<>?/\|}{~:']"

for i in ch:
    if(bin.count("i") == 0):
        pass
    else:
        print("Error : Enter Binary Digits not special characters")
        exit(2)

# Check for only digits 0 and 1
# Dismiss any other digits
for i in bin:
    # Check if numbers are less then 0
    if i < '0' or i > '1':
        print("Error : Enter Binary digits(0 or 1) not any other digits.")
        exit(3)

#A counter to count the number of loops we have have finished
count = 0

alert = "01"

# A list to save the previous digit.
lastone = []

#A variable to save the the number of times consecutive 0's
drac = []

# A list to temporarily save the zeroes
zeroes = []

pre = 0
prev = int

for i in bin:
    # We check if the previous number is 0.
    # But to do so we have to be on the 2nd digit in the bin
    # Or the loop should atleast have run once
	if not count == 0:
		pre = count - 1
		prev = lastone[pre]
	
	# incrementing the counter
	count += 1
    #if we hit a 1 we'll just pass or continue with our program.
	if i == 1:
		pass

    # Check if the current digit which is i = 0
    # If so add a 0 to a list called zeroes
	elif i == '0':
		zeroes.append('0')

    # TO check if we hit a 1 and if so check if the previous digit was 0
    # If so the to count the number of 0's we've saved in the zeroes list
    # Then to append that number in another list called drac
    # Empty the zeroes list using clear() method
	if prev == '0' and i == '1':
		drac.append(zeroes.count('0'))
		zeroes.clear()
	if count == total:
		drac.append(zeroes.count('0'))
		zeroes.clear()
	lastone.append(i)
    
max = sorted(drac)
if not total == 2:
	maxer = max[-1]
	print("The number of longest consecutive zeroes are ", maxer)
else:
	print("Error : Atleast provide two digits")
