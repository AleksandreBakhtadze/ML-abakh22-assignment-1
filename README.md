# ML-abakh22-assignment-1
////////////////////////House Prices - Advanced Regression Techniques////////////////////////
კონკურსის ფარგლებში უნდა გვეწინსაწარმეტყველებინა სახლების ფასები სხვადასხვა მონაცემების მიხედვით
გვქონდა 1460 სტრიქონი 81 სვეტი train data set-ში. სვეტები შეიცავდა როგორც numerical სცეტებსა ასევე categorical სვეტებს.
ხოლო test data set-სე გვქონდა 1459 სტრიქონი და 80 სვეტი. traget სვეტი იყო 'SalePrice' (სწორედ ეს სვეტი უნდა დაგვეგენერირებინა საუკეთესო მოდელით)
პრობლემის გადასაჭრელად სტანდარტულად გამოვიყენე Feature Engineering, Feature Selection, Training.

/////////////რეპოზიტორში არსებული ფაილები/////////////

model_experiment.ipynb 

ამ ფაილში თითოეულ ნაბიჯზე ნაცადი მიდგომების კოდები არის დაკომიტებული.Cleaning, Feature Engineering, Feature Selection და Trainin ნაბიჯებით (გამოყოფილი კომენტარებით)  

model_inference.ipynb 

ამ ფაილში კი მაქვს საბოლოოდ შერჩეული მოდელის დალოუდებისა , SalePrice-ის დაფრედიქთების და სადაბმითების კოდი


/////////////Feature Engineering/////////////
  
  კატეგორიული ცვლადების რიცხვითში გადაყვანა:
  
  ჯერ ვამუშავებდი null მნიშვნელობებს ყველა სვეტში. შემდგომ კი ვიყენებდი 8-9 სემინარზე გარჩეულ კოდს სადაც ვიყენებთ WOE და OHE-ს.
  threshlod ავიღე 3. ანუ სვეტებში რომლებშიც 3ზე მეტი განსხვავებული მნიშვნელობის ცვლადები იყო ვამუშავებდი WOE-თი ხოლო რომელშიც 3 ან ნაკლები OHE-თი. 
  
  Nan მნიშვნელობების დამუშავება
  
  numerical-ების შემთხვევასი ull -ები ჩავანაცვლე 0 ებით რადგან უმეტესი სვეტის მნიშვნელობა იყო რაიმეს ფართობი ან რაოდენობა ამიტო null-ების 0ებით შეცვლა უფრო ლოგიკურად ჩავთვალე 
  კატეგორიულების შემთხვევაში კი null-ებს უბრალოდ 'NO' სტრინგით ვცვლიდი. რადგან ამ შემთხვევაშიც უფრო ლოგიკური მეჩვენა მათი სხვა ახალი ცვლადით ჩანაცვლება.
  ასევე ვცადე მოდით და მედიანებით ჩანაცვლება მაგრამ ამას არანაირი გავლენა არ მოუხდებია საბოლოო შედეგზე.
  
  Cleaning მიდგომები
  
  ვდროპავდი ისეთ სვეტებს რომლებშიც missing values იყო 80% ან მეტი.


/////////////Feature Selection/////////////
  
  აქ გამოვიყენე ასევე 8-9 სემინარზე გარჩეული კოდი რომელშიც ვიყენებდით კორელაციასა და RFE-ის.
  კორელაციით დაგენერირებული კორელირებული სვეტები დავდროპე. და შემდეგ გამოვიყენე RFE რომელსაც ვაგენერირებინებდი 15 საუკეთესო სვეტს

  
/////////////Training/////////////
  
  ზემოთ ნახსენები მიდგომებისგან ავაწყვე pipeline რომლითაც ვტესტავდი სხვადასხვა მოდელებს. მოდელების ჰიპერპარამეტრების ოპტიმიზაციისთვის გამოვიყენე grid search 
  მაგრამ სამწუხაროდ ამის ამსახველი კოდები არ ამიტვირთავს თავიდან და შემდგომ დამეკარგა. grid search-მა მოდელები საბოლოოდ ვერ გააუმჯობესა მაგრამ დრო  გაზარდა ფრედიქშენის.
  საბოლოოდა გამოვიყენე მოდელები: LinearRegression, RandomForestRegressor, XGBRegressor, GradientBoostingRegressor. ყველა მოდელის მუშაობის პრინციპი ლექცია სემინარებზე გვაქვს განხილული.
  მოდელების შესაფასებლად კი ვიყენებდით სამ metric-ს RMSE , Bias , Varianc. გვინდოდა სამივე მეტრიკის მინიმიზაცია (0-თან ახლოს ყოფნა).

/////////////Mlflow/////////////
  
  პლატფორმაზე ატვირთულია თითოეული მოდელის პარამეტრები და მეტრიკები. რომლებიდანაც საუკეთესო აღმოჩნდა GradientBoostingRegressor რომელმაც მოგვცა ყველაზე დაბალი RMSE 0.135.
  ასევე ატვირთული მაქვს RFE ნახაზები მაგრამ თოთოეული მოდელისთვის ცალკე ექსპერიმენტებში ატვირთვა მოვახერხე მხოლოდ.  

  მოდელების ბმულები:

  LinearRegression    
  
  https://dagshub.com/AleksandreBakhtadze/ML-abakh22-assignment-1.mlflow/#/experiments/0/runs/e33ca8af037543beb64dfca58d3b0072

  RandomForestRegressor   
  
  https://dagshub.com/AleksandreBakhtadze/ML-abakh22-assignment-1.mlflow/#/experiments/2/runs/7ff319b99d0546968037d65eb5b826bb

  RandomForestRegressor RFE plots :)  

  https://dagshub.com/AleksandreBakhtadze/ML-abakh22-assignment-1.mlflow/#/experiments/1/runs/672fd3e8f5804df9addc4020e46f831c/artifacts

  XGBRegressor  

  https://dagshub.com/AleksandreBakhtadze/ML-abakh22-assignment-1.mlflow/#/experiments/3/runs/ac345f35d0844ef497d5ab3ef6878c05

  XGBRegressor RFE plots

  https://dagshub.com/AleksandreBakhtadze/ML-abakh22-assignment-1.mlflow/#/experiments/1/runs/5670aebf3a114d28b78714438c40a3df

  GradientBoostingRegressor    

  https://dagshub.com/AleksandreBakhtadze/ML-abakh22-assignment-1.mlflow/#/experiments/5/runs/88bcc47dda454073b1f79521098bdd08
  
   GradientBoostingRegressor  RFE plots   

   https://dagshub.com/AleksandreBakhtadze/ML-abakh22-assignment-1.mlflow/#/experiments/4/runs/e33f7a91483543edae114739635c64f0
  
