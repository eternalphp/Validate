		$_POST["title"] = "标题标题标题标题标题";
		$_POST["content"] = "内容内容";
		
		$validate = new Validate();
    
		$validate->make(function($rule){
			$rule->field("title");
			$rule->rule("required")->message("标题不能为空");
			$rule->rule("chinese")->message("标题必须包含中文");
			$rule->rule("maxlength")->value(10)->message("标题长度不能少于10");
		});
		
		$validate->make(function($rule){
			$rule->field("email");
			$rule->rule("required")->message("邮件地址不能为空");
			$rule->rule("email")->message("邮件地址不正确");
		});
		
		$result = $validate->validate($_POST,function($errors){
			 print_r($errors);
		});
