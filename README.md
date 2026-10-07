s = input()
arr=[]
check = "hello"
nxt = 0
for char in s:
  ch = check[nxt]
  if char == ch:
    nxt += 1
    arr.append(char)
  if nxt >= len(check):
    break
if "".join(arr) == check:
  print("YES")
else:
  print("NO")
