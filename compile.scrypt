contract CTC {
    static const int N = 4;
    static const int LOOPCOUNT = 30;

    // A is not a CTC because the right hand size is an expression, not a literal
    static const int A = 2 + 1;
    // B is not a CTC because it is not static
    const int B;

    // FC is a CTC declared in function parameters
    // it can be used within this function, including parameters after it & return type
    function incArr(static const int FC, int[FC] x) : int[FC] {
        loop(FC): i {
            x[i] += i; // induction variable CTC
        }
        return x;
    }

    public function unlock(int y) {
        int[N] arr0 = [1, 2, 3, 4];
        // use `N` to initialize CTC parameter `FC` of function `incArr`
        int[N] arr1 = this.incArr(N, repeat(1, N));
        loop(N) : i {
            require(arr0[i] == arr1[i]);
        }

        int z = 0;
        loop (LOOPCOUNT)
        {
            if (z<y) z += 4;
        }
        require(y == 1);
    }
}
