---
layout: post
title: Hex change
description: "将16进制的颜色值和透明度转换为 filter 所使用的十进制"
modified: 2014-12-21
tags: [tools]
image:
  feature: abstract-3.jpg
  credit: dargadgetz
  creditlink: http://www.dargadgetz.com/ios-7-abstract-wallpaper-pack-for-iphone-5-and-ipod-touch-retina/
---

<div class="wrap">
	<div><label for="class-name">样式名：</label><input type="text" value="" id="class-name"  /></div>
	<div><label for="color_value">需要透明的颜色十六进制值：#</label><input type="text" value="" id="color_value" maxlength="6" /></div>
	<div><label for="original">透明度：</label><input type="input" id="original" /></div>
	<button type="button" onclick="change_10_to_16()" class="btn btn-success">转为16进制的颜色</button>
	<br />
	<div id="alpha_style"></div>
</div>

<script type="text/javascript">
  var oOriginal = document.getElementById("original");
  var co_value = document.getElementById("color_value");
  var css_cont = document.getElementById("alpha_style");
  var warn_tip = document.getElementById("tip");
  var warn_tip_a = document.getElementById("tip_alphe");
  var classVal = document.getElementById("class-name");

  function change_10_to_16() {
      var pattern = /^[0-9a-fA-F]{6}$/;
      var pattern_3 = /^[0-9a-fA-F]{3}$/;
      var co = co_value.value;
      var num = Math.floor((Math.floor(oOriginal.value * 100) / 100) * 255);
      var num_10 = (Math.floor(oOriginal.value * 100) / 100);
      var num_change = num.toString(16);
      var txt = '';
      num = parseInt(num);
      if (co.match(pattern) == null) {
          if (co.length == 3) {
              if (co.match(pattern_3) == null) {
                  warn_tip.innerHTML = "十六进制是从【0】到【9】以及【a】到【f】组合而成的，再来一次吧！\n如果是十六进制的缩写，是前后相邻的字母可简写成为一个，例如【#FF000FF】可转为【#F0F】\n请检查你的颜色值是否为【三位】或者符合【十六进制的组合方式】。";
              } else {
                  if (oOriginal.value >= 0 && oOriginal.value <= 1) {
                      if (num_change.length == 1) {
                          num_change = "0" + num_change;
                      }
                      var co_a = co.substring(0, 1);
                      var co_b = co.substring(1, 2);
                      var co_c = co.substring(2, 3);
                      var co_a2 = co_a + co_a;
                      var co_b2 = co_b + co_b;
                      var co_c2 = co_c + co_c;
                      co = co_a2 + co_b2 + co_c2;
                      var outText="";
              if(classVal.value==""){
                  outText="filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "', endColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "');background:rgba(" + parseInt(co_a2, 16) + "," + parseInt(co_b2, 16) + "," + parseInt(co_c2, 16) + "," + num_10 + ");";
              }else{
                outText=classVal.value+"{filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "', endColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "');background:rgba(" + parseInt(co_a2, 16) + "," + parseInt(co_b2, 16) + "," + parseInt(co_c2, 16) + "," + num_10 + ");}";
                      outText+="<br /> :root "+classVal.value+"{filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#00" + co.toUpperCase() + "', endColorstr='#00" + co.toUpperCase() + "');}/*for IE9*/";
              outText+="<br />或者ie9的hack使用： <br /> :root "+classVal.value+"{filter:none;}/*for IE9*/";
              }
                      css_cont.innerHTML = outText;
                      /*temp_cont = css_cont.value;
                      txt += css_cont.innerHTML;
                      if (css_cont.value == "" || css_cont.value != txt) {
                          css_cont.value = txt;
                      }*/
                  } else {
                      warn_tip_a.style.display = "block";
                      warn_tip_a.innerHTML = "透明度的值在【0】到【1】之间。";
                  }
              }
          } else {
              warn_tip.style.display = "block";
              warn_tip.innerHTML = "十六进制是从【0】到【9】以及【a】到【f】组合而成的，再来一次吧！\n如果是十六进制的缩写，是前后相邻的字母可简写成为一个，例如【#FF000FF】可转为【#F0F】\n请检查你的颜色值是否为【三位】或者符合【十六进制的组合方式】。";
          }
      } else {
          if (oOriginal.value >= 0 && oOriginal.value <= 1) {
              if (num_change.length == 1) {
                  num_change = "0" + String(num_change);
              }
              var co_a = co.substring(0, 2);
              var co_b = co.substring(2, 4);
              var co_c = co.substring(4, 6);
              var outText="";
              if(classVal.value==""){
                  outText="filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "', endColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "');background:rgba(" + parseInt(co_a, 16) + "," + parseInt(co_b, 16) + "," + parseInt(co_c, 16) + "," + num_10 + ");";
              }else{
                outText=classVal.value+"{filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "', endColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "');background:rgba(" + parseInt(co_a, 16) + "," + parseInt(co_b, 16) + "," + parseInt(co_c, 16) + "," + num_10 + ");}";

                outText+="<br /> :root "+classVal.value+"{filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#00" + co.toUpperCase() + "', endColorstr='#00" + co.toUpperCase() + "');}/*for IE9*/";
                  outText+="<br />或者ie9的hack使用： <br /> :root "+classVal.value+"{filter:none;}/*for IE9*/";
              }
              css_cont.innerHTML = outText;
              //css_cont.innerHTML = "filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "', endColorstr='#" + num_change.toUpperCase() + co.toUpperCase() + "');background:rgba(" + parseInt(co_a, 16) + "," + parseInt(co_b, 16) + "," + parseInt(co_c, 16) + "," + num_10 + ");";
              temp_cont = css_cont.value;
              txt += css_cont.innerHTML;
              if (css_cont.value == "" || css_cont.value != txt) {
                  css_cont.value = txt;
              }
          } else {
              warn_tip_a.style.display = "block";
              warn_tip_a.innerHTML = "透明度的值在【0】到【1】之间。";
          }
      }
  }
</script>