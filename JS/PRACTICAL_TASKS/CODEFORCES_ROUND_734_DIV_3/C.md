# C. Interesting Story

Stephen Queen wants to write a story. He is a very unusual writer, he uses only letters 'a', 'b', 'c', 'd' and 'e'!

To compose a story, Stephen wrote out n words consisting of the first 5 lowercase letters of the Latin alphabet. He wants to select the maximum number of words to make an interesting story.

Let a story be a sequence of words that are not necessarily different. A story is called interesting if there exists a letter which occurs among all words of the story more times than all other letters together.

For example, the story consisting of three words "bac", "aaada", "e" is interesting (the letter 'a' occurs 5 times, all other letters occur 4 times in total). But the story consisting of two words "aba", "abcde" is not (no such letter that it occurs more than all other letters in total).

You are given a sequence of n words consisting of letters 'a', 'b', 'c', 'd' and 'e'. Your task is to choose the maximum number of them to make an interesting story. If there's no way to make a non-empty story, output 0.

[details >>>](https://codeforces.com/contest/1551/problem/C)

    const readNum = () => +readline();
    const readStr = () => readline();
    const readNumArr = () => readline().split(' ').map(item => +item);
    
    const n = readNum();
    
    for(var i = 0; i < n; i++) {
      var m = readNum();
      var bc = 0;
      var strs = [];
      var l = new Set();
      
      for(var j = 0; j < m; j++) {
        strs[j] = readStr();
        for(var k = 0; k < strs[j].length; k++) {
          l.add(strs[j][k]);
        }
      }
      
      for (var item of l) {
        var a = 0, b = 0, ans = [];
        for(var j = 0; j < m; j++) {
          var la = 0, lb = 0;
          for(var k = 0; k < strs[j].length; k++) {
            if(strs[j][k] === item) {
              la++;
            }
          }
          lb = strs[j].length - la;
          ans.push([la, lb, lb - la]);
          a += la;
          b += lb;
        }
        if(a > b) {
          bc = m;
          break;
        }
        ans.sort((a, b) => a[2] - b[2]);
        var t = m;
        while(t && t > bc) {
          t--;
          a -= ans[t][0];
          b -= ans[t][1];
          if(a > b) {
            bc = t;
            break;
          }
        }
      }
      
      print(bc);
    }
