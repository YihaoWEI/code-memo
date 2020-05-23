# code-memo
记录一些碎片化但有意义的代码们

## std::is_same<TypeA, TypeB>::value 
描述：可以在模板内部有效根据输入类型进行不同的操作区分。包含<type_traits>头文件。返回值是true/false。  
注意：char类型和signed和unsigned都是false。  
参考链接：https://blog.csdn.net/czyt1988/article/details/52812797  
实际代码：

```
  cv::Mat cv_input;
	if (std::is_same<InputType, uint8_t>::value)
		cv_input = cv::Mat(input.rows(), input.cols(), CV_8UC1, const_cast<InputType*>(input.data())); 
	else if (std::is_same<InputType, uint16_t>::value)
		cv_input = cv::Mat(input.rows(), input.cols(), CV_16UC1, const_cast<InputType*>(input.data())); 
```

## cv::integral(src, output, output_sqr)
描述：OpenCV已实现的积分图函数，可以输出线性积分和平方和积分  
注意：输出的长宽加1
实际代码：
```
	// Use sum table for sum and square sum.
	cv::integral(cv_input, cv_sum, cv_sum_sqr, CV_64F);
```  

	
