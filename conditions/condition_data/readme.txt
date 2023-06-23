dataset = scipy.io.loadmat(filename)
x = dataset['data']
y = dataset['labels'] #ntrials x 1 ----- (1, 2, 3, 4, 5, 6) -> (0, 1, 2, 3, 4, 5)

______________________________________________________________

          walk        |        dance 

1. cont               | 1. par
2. trist              | 2. soz             } S
3. norm               | 3. abn
---------------------------------------
4. cont               | 4. par
5. trist              | 5. soz             } P
6. norm               | 6. abn
