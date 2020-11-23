.. code:: sh

    %%sh
    apt-get install -y unzip
    wget https://sagemaker-sample-data-us-west-2.s3-us-west-2.amazonaws.com/autopilot/direct_marketing/bank-additional.zip
    unzip -o bank-additional.zip


.. parsed-literal::

    Reading package lists...
    Building dependency tree...
    Reading state information...
    unzip is already the newest version (6.0-23+deb10u1).
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    Archive:  bank-additional.zip
       creating: bank-additional/
      inflating: bank-additional/bank-additional-names.txt  
      inflating: bank-additional/bank-additional.csv  
      inflating: bank-additional/bank-additional-full.csv  


.. parsed-literal::

    --2020-11-23 21:56:42--  https://sagemaker-sample-data-us-west-2.s3-us-west-2.amazonaws.com/autopilot/direct_marketing/bank-additional.zip
    Resolving sagemaker-sample-data-us-west-2.s3-us-west-2.amazonaws.com (sagemaker-sample-data-us-west-2.s3-us-west-2.amazonaws.com)... 52.218.192.25
    Connecting to sagemaker-sample-data-us-west-2.s3-us-west-2.amazonaws.com (sagemaker-sample-data-us-west-2.s3-us-west-2.amazonaws.com)|52.218.192.25|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 432828 (423K) [application/zip]
    Saving to: ‘bank-additional.zip’
    
         0K .......... .......... .......... .......... .......... 11%  412K 1s
        50K .......... .......... .......... .......... .......... 23%  136M 0s
       100K .......... .......... .......... .......... .......... 35%  780K 0s
       150K .......... .......... .......... .......... .......... 47% 61.5M 0s
       200K .......... .......... .......... .......... .......... 59%  793K 0s
       250K .......... .......... .......... .......... .......... 70%  116M 0s
       300K .......... .......... .......... .......... .......... 82% 89.7M 0s
       350K .......... .......... .......... .......... .......... 94% 97.2M 0s
       400K .......... .......... ..                              100%  115M=0.3s
    
    2020-11-23 21:56:43 (1.64 MB/s) - ‘bank-additional.zip’ saved [432828/432828]
    


.. code:: ipython3

    import pandas as pd
    data = pd.read_csv('./bank-additional/bank-additional-full.csv')
    data[:10]




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>age</th>
          <th>job</th>
          <th>marital</th>
          <th>education</th>
          <th>default</th>
          <th>housing</th>
          <th>loan</th>
          <th>contact</th>
          <th>month</th>
          <th>day_of_week</th>
          <th>...</th>
          <th>campaign</th>
          <th>pdays</th>
          <th>previous</th>
          <th>poutcome</th>
          <th>emp.var.rate</th>
          <th>cons.price.idx</th>
          <th>cons.conf.idx</th>
          <th>euribor3m</th>
          <th>nr.employed</th>
          <th>y</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>56</td>
          <td>housemaid</td>
          <td>married</td>
          <td>basic.4y</td>
          <td>no</td>
          <td>no</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>1</th>
          <td>57</td>
          <td>services</td>
          <td>married</td>
          <td>high.school</td>
          <td>unknown</td>
          <td>no</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>2</th>
          <td>37</td>
          <td>services</td>
          <td>married</td>
          <td>high.school</td>
          <td>no</td>
          <td>yes</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>3</th>
          <td>40</td>
          <td>admin.</td>
          <td>married</td>
          <td>basic.6y</td>
          <td>no</td>
          <td>no</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>4</th>
          <td>56</td>
          <td>services</td>
          <td>married</td>
          <td>high.school</td>
          <td>no</td>
          <td>no</td>
          <td>yes</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>5</th>
          <td>45</td>
          <td>services</td>
          <td>married</td>
          <td>basic.9y</td>
          <td>unknown</td>
          <td>no</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>6</th>
          <td>59</td>
          <td>admin.</td>
          <td>married</td>
          <td>professional.course</td>
          <td>no</td>
          <td>no</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>7</th>
          <td>41</td>
          <td>blue-collar</td>
          <td>married</td>
          <td>unknown</td>
          <td>unknown</td>
          <td>no</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>8</th>
          <td>24</td>
          <td>technician</td>
          <td>single</td>
          <td>professional.course</td>
          <td>no</td>
          <td>yes</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
        <tr>
          <th>9</th>
          <td>25</td>
          <td>services</td>
          <td>single</td>
          <td>high.school</td>
          <td>no</td>
          <td>yes</td>
          <td>no</td>
          <td>telephone</td>
          <td>may</td>
          <td>mon</td>
          <td>...</td>
          <td>1</td>
          <td>999</td>
          <td>0</td>
          <td>nonexistent</td>
          <td>1.1</td>
          <td>93.994</td>
          <td>-36.4</td>
          <td>4.857</td>
          <td>5191.0</td>
          <td>no</td>
        </tr>
      </tbody>
    </table>
    <p>10 rows × 21 columns</p>
    </div>



.. code:: ipython3

    import sagemaker
    
    prefix = 'sagemaker/tutorial-autopilot/input'
    sess   = sagemaker.Session()
    
    uri = sess.upload_data(path="./bank-additional/bank-additional-full.csv", key_prefix=prefix)
    print(uri)


.. parsed-literal::

    s3://sagemaker-us-east-1-965762646475/sagemaker/tutorial-autopilot/input/bank-additional-full.csv

