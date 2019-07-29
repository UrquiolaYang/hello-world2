
---
### . LM Error Corrector

#### 功能简介

- 修正指定语言模型中的substitutions错误
- 修正指定语言模型中的某个gram的loglikelihood

#### 参数详解&用例

参数详解

    ('--correct_word', default='无', help='正确的词')
	('--wrong_word', default='五', help='错误的词')
	('--value_scale', type=float, default=0.7, help='修改幅度')
	('--original_lm', default='/data/app/ron/neural-architecture-search/lm/3gram.kn111.up', help='当前语言模型的路径')
	('--modified_lm', default='/data/app/ron/neural-architecture-search/lm/new_ngram_lm_tri', help='修改后语言模型输出路径')
	('--mul_grams', default='吴，总，银行', help='用于输入bigram或者trigram，用中文逗号代替空格')
	('--mul_grams_logpro',type=float, default=-10, help='修改bigram或者trigram为指定值')

- 

- 用法实例1 

修正substiution错误 输入一对词(unigram)，正确的unigram提高
，根据输入的语言模型，取这对词共同的ngram，以修改幅度value_sacle提升正确词ngram的loglikelihood，降低错误词ngram的loglikelihood：

	python modify_lm.py --correct_word 无 --wrong_word 五 --value_scale 0.7 --original_lm /data/app/yangyf/lm/3gram.kn111.up --modified_lm /data/app/yangyf/lm/new_ngram_lm4

- 用法实例2 

输入一个unigram或bigram或trigram，直接修改ngram的loglikelihood

	python modify_lm.py --mul_grams '吴，总，银行' --mul_grams_logpro -10 --original_lm /data/app/yangyf/lm/3gram.kn111.up --modified_lm /data/app/yangyf/lm/new_ngram_lm4

- 注意

当传入参数

	--correct_word neg_modify 
则不修正substiution错误，

	--opt.mul_grams neg_modify
则不单独修正某个gram的logLikelihood

#### 环境依赖

- python3

#### 准备工作

- 当前语言模型的路径；

#### 代码路径

---
