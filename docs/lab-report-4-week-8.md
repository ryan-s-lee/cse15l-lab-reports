
UCSD CSE 15L Week 8 Lab Report 4: Github Access from ieng6 (Choice 2)
========================
## Links to tested repos
[My repo](www.example.com)  
[Reviewed Repo](www.example.com)  

## Test 1
### Expected output
![snippet1preivew](assets/images/lab4/snippet1preview.png)  
```
[`google.com, google.com, ucsd.edu]  
```
### Test code
![test1code](assets/images/lab4/test1code.png)  
### My implementation's results
![my1result](assets/images/lab4/my1result.png)  
### Reviewed repo's results
![review1result](assets/images/lab4/review1result.png)

## Test 1
### Expected output
![snippet2preivew](assets/images/lab4/preview2snippet.png)  
```
[a.com, a.com(()), example.com]
```
### Test code
![test2code](assets/images/lab4/test2code.png)
### My implementation's results
![my2result](assets/images/lab4/my2result.png)  
### Reviewed repo's results
![review2result](assets/images/lab4/review2result.png)

## Test 1
### Expected output
![snippet3preivew](assets/images/lab4/preview3snippet.png)  
```
```
### Test code
![test3code](assets/images/lab4/test3code.png)
### My implementation's results
![my3result](assets/images/lab4/my3result.png)  
### Reviewed repo's results
![review3result](assets/images/lab4/review3result.png)

## Workload of Correcting Errors
### Snippet 1
Adapting my current code to account for backticks and code blocks should take less than 10 lines. I should only have to check if a backtick exists before the open bracket, and see if it has a matching backtick inside the link definition, in which case the link should not be valid.
### Snippet 2
My code would likely need moderate refactoring in order to account for nested parentheses and brackets. I would likely have to write code that can match parentheses, which is an entire algorithm have to implement, as well as what to do when parentheses/brackets aren't properly paired. However, checking for escaped characters and skipping them should be easy since I only have to check for a backtick before characters of significance like brackets.  
### Snippet 3
The thing that is being tested in snippet 3, which is multi-line titles and links, should be easy to account for. I simply don't check for newlines in the title, but do check for newlines in the link (and consider the link invalid if they appear before the closing parenthesis). The IndexOutOfBounds exception I got should also be a <10 line fix because I believe I only have to do more indexOf = -1 checks for characters I haven't already done it for.