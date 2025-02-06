import excel "C:\Users\aulavirtual\Downloads\BUENA DATASET GLOB INDEPEDENT VARIABLE .xlsx", sheet("Sheet1") firstrow case(lower)
summarize
describe
rename howimportantisgodinyourlif god_importance
rename nationalpride national_pride
rename autonomyindex autonomy
rename justifiableabortion abortion
rename futurechangesrespectforauth respect_for_auth
rename politicalactionsigningapeti petition_action
rename postmaterialistindex4item postmaterialism
rename mostpeoplecanbetrusted trust
rename feelingofhapiness happiness
rename justifiablehomoxesuality homosexuality
browse
drop if _n >= 93
rename country countryname
save "C:\Users\aulavirtual\Downloads\BUENA_DATASET_GLOB_INDEPENDENT_VARIABLE_CLEANED.dta", replace
import excel "C:\Users\aulavirtual\Downloads\Copy of P_Internet Penetration over time.xlsx", sheet("Data") firstrow case(lower) clear
describe
encode country, gen(country_string)
browse
rename yr2017 penetrationrate_2017
rename yr2018 penetrationrate_2018
rename yr2019 penetrationrate_2019
rename yr2020 penetrationrate_2020
rename yr2021 penetrationrate_2021
rename yr2022 penetrationrate_2022
rename yr2023 penetrationrate_2023
drop country_string
drop if _n >= 214
reshape long penetrationrate_, i(countryname) j(year)
destring penetrationrate_, replace force
browse
save "C:\Users\aulavirtual\Downloads\Copy of P_Internet Penetration over time_CLEANED.dta", replace
merge 1:1 countryname year using "C:\Users\aulavirtual\Downloads\BUENA_DATASET_GLOB_INDEPENDENT_VARIABLE_CLEANED.dta"
keep if _merge == 3
drop seriesname
ssc install asdoc
asdoc summarize, replace
summarize god_importance national_pride autonomy abortion respect_for_auth petition_action postmaterialism trust happiness homosexuality penetrationrate_
asdoc correlate god_importance national_pride autonomy abortion respect_for_auth petition_action postmaterialism trust happiness homosexuality penetrationrate_
asdoc regress penetrationrate_ god_importance national_pride autonomy abortion respect_for_auth petition_action postmaterialism trust happiness homosexuality
asdoc regress god_importance penetrationrate_
asdoc regress national_pride penetrationrate_
asdoc regress autonomy penetrationrate_
asdoc regress abortion penetrationrate_
asdoc regress respect_for_auth penetrationrate_
asdoc regress petition_action penetrationrate_
asdoc regress postmaterialism penetrationrate_
asdoc regress trust penetrationrate_
asdoc regress happiness penetrationrate_
asdoc regress homosexuality penetrationrate_
scatter god_importance penetrationrate_
drop _merge
save "C:\Users\aulavirtual\Downloads\Copy of P_Internet Penetration over time_DEPENDENT.dta", replace
import excel "C:\Users\aulavirtual\Downloads\control variables.xlsx", sheet("Sheet1") firstrow case(lower) clear
drop if _n >= 267
save "C:\Users\aulavirtual\Downloads\control variables.xlsx_CLEANED.dta", replace
merge 1:1 countryname using "C:\Users\aulavirtual\Downloads\Copy of P_Internet Penetration over time_DEPENDENT.dta"
keep if _merge == 3
asdoc summarize
asdoc corr penetrationrate_ god_importance national_pride autonomy abortion respect_for_auth petition_action postmaterialism trust happiness homosexuality gdppercapita education urbanization
asdoc regress penetrationrate_ urbanization gdppercapita education god_importance national_pride autonomy abortion respect_for_auth petition_action postmaterialism trust happiness homosexuality
asdoc regress god_importance penetrationrate_ gdppercapita education urbanization
asdoc regress national_pride penetrationrate_ gdppercapita education urbanization
asdoc regress autonomy penetrationrate_ gdppercapita education urbanization
asdoc regress abortion penetrationrate_ gdppercapita education urbanization
asdoc regress respect_for_auth penetrationrate_ gdppercapita education urbanization
asdoc regress petition_action penetrationrate_ gdppercapita education urbanization
asdoc regress postmaterialism penetrationrate_ gdppercapita education urbanization
asdoc regress trust penetrationrate_ gdppercapita education urbanization
asdoc regress happiness penetrationrate_ gdppercapita education urbanization
asdoc regress homosexuality penetrationrate_ gdppercapita education urbanization
graph matrix penetrationrate_ god_importance national_pride autonomy abortion respect_for_auth homosexuality petition_action postmaterialism happiness trust gdppercapita education urbanization
asdoc graph matrix penetrationrate_ god_importance national_pride autonomy abortion respect_for_auth homosexuality petition_action postmaterialism happiness trust gdppercapita education urbanization

