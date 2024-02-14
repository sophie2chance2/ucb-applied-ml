```
for row in data:
    tmp_row = []
    for entry in row:
        tmp_row.append(float(entry))
    output.append(tmp_row)

M = np.array(output)

for idx, entry in enumerate(col_names):
    plt.hist(M[:,idx])
    plt.title(entry)
    plt.show()

L = M[:,-1]
M = M[:,:-1]

from sklearn.ensemble import RandomForestRegressor
clf = RandomForestRegressor()
clf.fit(M[:1000, :], L[:1000])

clf.score(M[1000:], L[1000:])

from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier()
clf.fit(M[:1000, :], L[:1000])

clf.score(M[1000:], L[1000:])

from collections import Counter
Counter(zip(clf.predict(M[1000:]), L[1000:]))


clf = RandomForestClassifier()
clf.fit(M[:1000, :], [1 if x>6 else 0 for x in L[:1000]])

clf.score(M[1000:], [1 if x>6 else 0 for x in L[:1000]])

clf.feature_importances_
print(zipcol_names, clf.feature_importances_))

```