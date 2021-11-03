# A. Polycarp and Coins

Polycarp must pay exactly n burles at the checkout. He has coins of two nominal values: 1 burle and 2 burles. Polycarp likes both kinds of coins equally. So he doesn't want to pay with more coins of one type than with the other.

Thus, Polycarp wants to minimize the difference between the count of coins of 1 burle and 2 burles being used. Help him by determining two non-negative integer values c1 and c2 which are the number of coins of 1 burle and 2 burles, respectively, so that the total value of that number of coins is exactly n (i. e. c1+2⋅c2=n), and the absolute value of the difference between c1 and c2 is as little as possible (i. e. you must minimize |c1−c2|).

[details >>>](https://codeforces.com/contest/1551/problem/A)

    function polycarpAndCoins(coins) {
      var a1 = Math.floor(coins / 3);
      var a2 = coins % 3;
      if(a2 === 2) {
        return a1 + " " + (a1 + 1);
      }
      if(a2 === 1) {
        return (a1 + 1) + " " + a1;
      }
      return a1 + " " + a1;
    }

    const readNumber = () => +readline();

    const n = readNumber();
    for(var i = 0; i < n; i++) {
      print(polycarpAndCoins(readNumber()));
    }
