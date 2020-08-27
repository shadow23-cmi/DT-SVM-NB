# DT-SVM-NB

CLASSIFICATION PROBLEM with
DECISION TREE,SVM,NAIVE BAYESIAN CLASSIFIER

 
ABOUT:
	We created a ipython project with kernel python 3.7 on a data set availavle at: https://archive.ics.uci.edu/ml/datasets/Bank+Marketing .
We have used the  bank-additional-full.csv file .
The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution.The classification goal is to predict if the client will subscribe a term deposit (variable y).We have made 3 classification models : A Dicision Tree ,
A Support Vector Machine and a Naive Bayesian classifier.

Libraries :
	The following python3 libraries have been used:
		numpy 
		pandas 
		time
		math
		sklearn.tree.DecisionTreeClassiier
		sklearn.model_selectio.cross_validate
		sklearn.model_selection.train_test_split
		sklearn.metrics.accuracy_score
		sklearn.metrics.precision_recall_fscore_support
		sklearn.neighbors.DistanceMetric

PARAMTERS USED:
	For Decision Tree,
		Max depth of tree =7,(To avoid overfitting)
		Min Samples in a leaf =50,
		Criterion = Gini Index
	    and Class weightage ={yes:2,No:1}
	For SVM,
		Kelnel = RBF
		class weightage={yes:2.35,No:1}
	For Naive Bayesian,
		no parameters have been taken as input.

PROGRAM DESCRIPTION:
	Funcions:
		sampling(dataframe,percentage):
			returnes percentage% of the dataframe after sampling

		preprocess_word_to_num(dataframe):
			takes a dataframe as input and returnes a dataframe with all word class features mapped to numeric class features.
		      A simple Example:
			     if column=="y":
				df_copy[column]=df_copy[column].replace({"yes":1,"no":0})

		normalize(dataframe):
			Normalize all the numeric fearure data pts in the dataframe by
		      replacing xi with (xi - ū )/σ where, ū : feature mean, σ: feature standerd deviation. 

(N.B: NORMALIZATIO IS IMPORTANT SVM AS OTHERWISE IT SVM CANT CLUSTER THE DATA UNBAISEDLY)
		drop_column(dataframe,col):
			Drops unnecessary features from dataframe.
	
	
	Clustering:
		The idea:
			Since most people spend according to their income,their agreeing to a term deposit depends greatly on monthly savings 				capability. In a consumer based economy,the savings of a person greatly varies on the price of daily necessary household 				items, employment and other economic conditions.Consumer price index, consumer confidence index,employment variation rate 				greatly estimate these factors.

		The clustering:
				Since the data is skewd with outcome results no:yes =(approx)9:1 we needed to do undersampling , but random 				undersamplingmay loose important data.So,we have divided the dataset on monthly  basis and measured  distance of each pair 				of data points based on taxi-cab metric,Thus data on consumer price index and other monthly and quarterly data are not lost.
			For every data point we have considered a 2 radius neighbourhood and if it contnains ≥ 4 pts in it then we have 			discarded all the points in that neighbourhood except the centre. Since,this way of clustering is very premitive some 				centers are also getting deleted.But by taking the neighbourhood radius =2 we are not discarding any whole 				cluster.

(N.B: WHILE CLUSTERING WE HAVE USED ONLY DATA PTS WITH NEGATIVE OUTCOME SO THAT THE DATA SET BECOMES BLANCED)

       Dropping features:
		Have dropped some features that were not contributing more to the classification.

(N.B: DURATON HAS NOT BEEN DROPPED)

       Model fitting and cross validation:
		We have used sklearn.model_selection.cross_validate for cross validation of the different model trained.

   OUTCOME:
	In decision tree we achived accuracy of ~ 0.87, recall ~ 0.82,precision ~ 0.63, fscore ~ 0.71 .
	In SVM we achived accuracy of ~ 0.87, recall ~ 0.83,precision ~ 0.6, fscore ~ 0.7 .
	In Naive bayesian we achived accuracy of ~ 0.81, recall ~ 0.63,precision ~ 0.51, fscore ~ 0.56.
	The detailed output is stored in: https://drive.google.com/drive/folders/1-c0UFsi4qBCb7fJ6qxstzZttHCa5sFon 


   CONCLUSION:
	The mdeels have used the "duration" feature,which implies this results can only be used as benchmarking on real-time predicting.
	
