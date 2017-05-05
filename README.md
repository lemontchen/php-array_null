# php-array_null
PHP递归方式把一个数组里面的null转换为空字符串”


在接口的调用中,直接查询数据库出来的字段可能为null字段，但是为了简便前端的判断,需要把null转换成空字符串'',这个时候就需要递归的方式进行

//把 null转换为空'' 递归方式

//$arr  ----   需要转换的数组

public function array_null($arr)
{
    
    if ($arr !== null) {
    
    		if (is_array($arr)) {//判断是不是数组--是数组
        
    			if (!empty($arr)) {
          
    				foreach ($arr as $key => $value) {
            
    					if ($value === null) {
              
    						$arr[$key] = '';
                
    					} else {
              
    						$arr[$key] = $this->array_null($value);		//递归再去执行
                
    					}
              
    				}
            
    			}else{ $arr = ''; }
          
    		} else {
        
    			if ($arr === null) { $arr = ''; }	//注意三个等号
          
    		}
        
    	} else { $arr = ''; }
      
    	return $arr;
      
    }
