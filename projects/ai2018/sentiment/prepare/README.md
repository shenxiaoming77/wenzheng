first sh ./gen-vocab.sh to get vocab.txt

then using like vocab-mincount.. to get vocab.5k.txt 
then merge with all chars from vocab.txt using vocab-add-char.py to get vocab.5k.chars.txt this is used for word embedding train  

then for canyin and dianping

just use ./gen-mix-seg-canyin.py  ./gen-char-seg-canyin.py ...
not use ./gen-seg-canyin.py for this project for we do not want to consider more words not used here  

do also for dianping and train/valid/test data  

we will use all these data as word embedding pretrain   

sh ./gen-vocab-v2.sh will use simple just basic seg   
NOTICE this is depreceated for v2
just use same vocab as v1, v2 only diff when gen tfrecord will not feed single and will has char embedding   

since v2 word + char concat prove to be better then seg basic + single so try to further try seperate word and char embedding as V3  
the script ./run-noemb-v3.sh is the same as ./run-noemb-v2.sh be sure you have char_vocab.txt under tfrecord dir    


3 seg method
1.char  char only 
2.word.feed  basic + digit + feed_sginle  only consider first 6k top freq word 
3.word.basic  basic  


now change to below process

1. seg for train+valid+test   
2. get vocab from train+valid+test   
3. generate tfrecord using seg result and vocab   

use 4 seg method with below name  
1. char  
2. mix(jieba)
3. word (jieba pos, should be word.jieba)  
4. besg(word by phrase bseg should be word.besg)

