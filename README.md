# HomeWork3

ამ კოდით ვქმნით ლოგისტიკურ რეგრესიას German Data Risk მონაცემებზე.
მე-15 სტრიქონზე ჩვენ ვაიმპორტირებთ ჩვენ მონაცემებს შემდეგი ბრძანებით:  df=pd.read_csv("http://archive.ics.uci.edu/ml/machine-learning-databases/statlog/german/german.data",sep=" ",header=None)
21-ე სტრიქონზე ჩვენ ვამოწმებთ გამოტოვებული მნიშვნელობები თუ გვაქვს შემდეგი ბრძანებით: df.isna().sum() . ბრძანება გვაჩვენებს რომ გამოტოვებული მნიშვნელობები არ გვაქვს
30-ე სტრიქონზე ჩვენ ვქმნით dummie სვეტებს კატეგორიული მონაცემებისთვის რომ ლოგისტიკურმა რეგრესიამ შეძლოს მისი გამოენება შემდეგი ბრძანებით: dummies = pd.get_dummies(df[[0, 2, 3,5,6,8,9,11,13,14,16,18,19]], prefix=['col0', 'col2', 'col3','col5','col6','col8','col9','col11','col13','col14','col16','col18','col19'])

შემდგომ sklearn-ის გამტენებით ჩვენ ვყობთ მონაცემებს 70/30 დაყოფით შემგეგი ბრძანებით: X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=0, stratify=y
)


შემდგომ ჩვენ ვქმნით ლოგისგიკურ რეგრესიას: 
model = LogisticRegression(max_iter=10000)
model.fit(X_train, y_train)

და საბოლოოდ ვამოწმებთ მოდელის ისზუსტეს:
y_pred = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
print("\nClassification Report:\n", classification_report(y_test, y_pred))

ესაა ძირითადი ნაბიჯები ამ დავალებისთვის
