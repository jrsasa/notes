- #[[latex 问题]]
-
1. 参考文献	总文件aux 工具 参考文献  点击 编译  再在总文件下点编译
2. 插图 \upcite{} \ref{} 公式() 公式中注意字母大小的统一
3. 正文 逗号（全角和半角之分)
4. \begin{table}[!h]  \caption{不同采样率下各重构算法重构时间比较(单位:s)}
	\centering
	\label{tab-alg4}
	\renewcommand\arraystretch{1.2}
	
	\begin{tabular}{ccccccc}  
		
		\toprule   
		
		采样率 &DGI&	FDRI&	  GD& AP&TVAL3\\
		
		\midrule   
		
		100\% & 44.3 &  1.64& 15.4 &20.3& 16.6\\
		50\% & 43.4 &  1.53&  14.3& 19.7& 15.4\\
		25\% & 42.1 &  1.94&  13.9& 18.7& 14.3\\
		12.5\% &  40.9&  1.45&  12.8& 19.6& 16.3\\
		
		\bottomrule  
		
	\end{tabular}
	
\end{table}
5.\begin{figure}[H]
	\centering
	\includegraphics[height=4.5in]{figure/chap5-fig/image46.eps}
	\caption{关联光谱成像系统实物图}
	\label{fig-sy1}
\end{figure}
H固定位置 !h灵活选位

常见错误

编译时
