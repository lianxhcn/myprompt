我有一些 {旧代码}，结果输出时写的很繁琐。我现在想修改成如下思路 {新代码思路}：
1. 使用 reghdfe 代替 reg 命令估计；
2. 使用 estfe m* 收集虚拟变量对应的标签
3. 最后再使用 esttab, indicate() 输出最终结果。最主要的是高效标记 Yes ， No

```stata
'''{新代码思路}
webuse "nlswork.dta", clear

reghdfe ln_wage age ttl_exp union, absorb(year)
est store m1

reghdfe ln_wage age ttl_exp union, absorb(ind_code)
est store m2

reghdfe ln_wage age ttl_exp union, absorb(race occ_code)
est store m3

reghdfe ln_wage age ttl_exp union, absorb(ind_code#year)
est store m4

* labels 括号内：左边是 absorb 的变量名，右边是你想在表格里显示的标签
estfe m*, labels(year "Year FE" ///
                 ind_code "Industry FE" ///
                 race "Race FE" ///
                 occ_code "Occupation FE" ///
                 ind_code#year "Industry-Year FE")

// 输出
esttab m*, nogap compress b(%6.3f) t(%6.2f) star(* 0.1 ** 0.05 *** 0.01) ///
    mtitle("(1)" "(2)" "(3)" "(4)") ///
    indicate(`r(indicate_fe)')  // 调用由 estfe 自动生成的宏
'''
```

随后我会发给你多个 {旧代码}，你帮我改成 {新代码思路} 的风格。

比如：

```stata
'''{旧代码}
reg green_inno AI , r 
estadd local year "No"
estadd local industry "No"
est store m1
reg green_inno AI  $control $controlCEO $controlP, r 
estadd local year "No"
estadd local industry "No"
est store m2
reg green_inno AI  $control $controlCEO $controlP i.industry i.year, r 
estadd local year "YES"
estadd local industry "YES"
est store m3
* Table 4-Baseline Regression*
esttab m1 m2 m3  using "Table4-BaselineRegression.rtf", ///
    replace  b(%12.3f) se(%12.3f) nogap  ///
    compress  drop(*.year *.industry)    ///
    s(N r2 ar2 industry year ) ///
    star(* 0.1 ** 0.05 *** 0.01) ///
    title (Table 4-Baseline Regression)
'''
```
