# Ecommerce Purchases Data Indights

To perform data analysis with Panda's, There are 15 questions that we are going to solve one by one. Questions & Pandas queries are as follows.

**1. Display Top 10 Rows of The Dataset**
=> data.head(10)

**2. Check Last 10 Rows of The Dataset**
=> data.tail(10)

**3. Check Datatype of Each Column**
=> data.dtypes

**4. Check null values in the dataset**
=> data.isnull().sum(axis=0)

**5. How many rows and columns are there in our Dataset?** 
=> data.shape

**6. Highest and Lowest Purchase Prices.**
=> Highest : data['Purchase Price'].max()
=> Lowest : data['Purchase Price'].min()

**7. Average Purchase Price**
=> data['Purchase Price'].mean()

**8. How many people have French 'fr' as their Language?**

   Using Length (Len) Method :
=> len(data[data['Language']== 'fr'])

   Using (count) Method
=> data[data['Language']== 'fr'].count()
  
**9. Job Title Contains Engineer**
=> len(data[data['Job'].str.contains('engineer',case=False)])

**10. Find The Email of the person with the following IP Address: 132.207.160.22**
=>  data[data['IP Address']=="132.207.160.22"]['Email']

**11. How many People have Mastercard as their Credit Card Provider and made a purchase above 50?**

    Using Length (Len) Method
=>  len(data[(data['CC Provider']=="Mastercard")&(data['Purchase Price']>50)])

    Using (count) Method
=>  data[(data['CC Provider']=="Mastercard") & (data['Purchase Price']>50)].count()

**12. Find the email of the person with the following Credit Card Number: 4664825258997302**
=>  data[data['Credit Card']== 4664825258997302]['Email']

**13. How many people purchase during the AM and how many people purchase during PM?**
=>  data['AM or PM'].value_counts()

**14. How many people have a credit card that expires in 2020?**

    Method 1 user def() function 
=>  def fun():
    count = 0
    for date in data ['CC Exp Date']:
        if date.split('/')[1]=='20':
            count=count+1
    print (count)

    Method 2 lambda function
=>  len(data[data['CC Exp Date'].apply(lambda x:x[3:]== '20')])

**15. What are the top 5 most popular email providers (e.g. gmail.com, yahoo.com, etc...)**

    Method 1 using Value counts method by adding new column to data frame
=>  list1 = []
    for email in data['Email']:
    list1.append(email.split('@')[1])
    data['temp']= list1
    data.head(1)

    data['temp'].value_counts().head(5)

    Method 2 using apply (Lambda x) Function
=>  data['Email'].apply(lambda x:x.split('@')[1]).value_counts().head()

**16. Which Credit Card Provider's cards has done the Most purchasing in terms of total value, Share top 5?**
=>  data.groupby('CC Provider')['Purchase Price'].sum().nlargest(5)


