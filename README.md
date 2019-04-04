<!DOCTYPE html>
<heml>

    <head>
        <meta name="viewport"
            content="width=device-width, initial-scale=1.0, minimum-scale=0.5, maximum-scale=2.0, user-scalable=yes" />
            <meta http-equiv="Content-Type" content="text/html; charset=utf-8"> 
    </head>

    <body>

        <h2>
            <p style="position:absolute;top:0%;width:100%; text-align:center">贷款计算器</p>
        </h2>
        <div id="page0" style="position:absolute;width:100%;height:100%;margin:10px; display:block;">
            <div style="position:absolute;top:5%; width:100%;height:100%;left:25%;background-color:peru">
                <h3 style="background-color :coral ;text-align:center;">申请条件</h3>
                <p style="position:absolute;left: 0%;">(1) 年龄22-55周岁</p><br>
                <p style="position:absolute;left: 0%;word-wrap:break-word;">(2) 非个人征信黑名单，且没有法院执行。</p><br><br>
                <h3 style="background-color :coral ;text-align:center;word-wrap:break-word;">申请人及担保人资料准备</h3>
                <p style="position:absolute;left: 0%;word-wrap:break-word;">(1) 证件类：夫妻双方身份证、户口本、结婚证</p><br>
                <p style="position:absolute;left: 0%;word-wrap:break-word;"> (2) 资产类：商品房产证（如有）、机动车行驶证（如有）</p><br>
                <p style="position:absolute;left: 0%;word-wrap:break-word;"> (3) 资信类：近6个月银行流水、个人征信报告（可至当地人民银行凭身份证办理）</p><br><br><br>
                <p style="position:absolute;right:0%; font-size:15px;word-wrap:break-word;">我已认真阅读以上资料并且满足以上条件  <input id="radio" type="radio"></p><br><br>
                <input type="button" value="进入计算器" onclick="init()"
                style="position:absolute;left: 30%; height:35px;font-size:25px"><br>               
            </div>
        </div>
        <div id="page1" style="position:absolute;width:100%;height:100%;top:10%;display:none;">
            <p style="position:absolute;right:20%;top:5%">单位（元）</p>
            <div name="myinput"
                style="position:absolute;width:100%;height:100%;text-align:center;top:12%;font-size:30px">
                * 机器总价
                <input type="number" id="TotalPrice" placeholder="此处填写机器总价"
                    style="height:25px;margin:10px;background-color: azure;width:20%"><br><br>
                * 首付比例
                <select id="DownPaymentRatio" style="height:25px;margin:10px;width:20%">
                    <option value="30">30%</option>
                    <option value="35">35%</option>
                    <option value="40">40%</option>
                    <option value="45">45%</option>
                    <option value="50">50%</option>
                    <option value="55">55%</option>
                    <option value="60">60%</option>
                    <option value="65">65%</option>
                    <option value="70">70%</option>
                </select><br><br>

                * 分期时间
                <select id="ByStages" style="height:25px;margin:10px;width:20%">
                    <option value="6">6个月</option>
                    <option value="12">12个月</option>
                    <option value="18">18个月</option>
                    <option value="24">24个月</option>
                    <option value="30">30个月</option>
                    <option value="36">36个月</option>
                </select>
                <br><br>
                * 服务费用
                <select id="Service" style="height:25px;margin:10px;width:20%">
                    <option value="2">2%</option>
                    <option value="3">3%</option>
                    <option value="4">4%</option>
                </select>
                <br><br>

                <input type="button" value="开始计算" onclick="Calculator()"
                    style="height:45px;width: 150px;font-size:30px"><br>
            </div>
        </div>


        <div id="page2" style="position:absolute;width:100%;top:10%;height: 100%;font-size:30px; display:none">

            <div style="position:absolute;width:70%;left:30%;top:10%">
                <p style="position:absolute;right:25%;top:0%;font-size:20px">单位（元）</p><br><br>
                * 融资贷款额
                <input type="number" id="LoanAmount"
                    style="height:30px;margin:10px;background-color: azure;width:20%;left: 0%;"><br>
                * 首付金额
                <input type="number" id="DownPaymentAmount"
                    style="height:30px;margin:10px;background-color: azure;width:20%;left: 0%"><br>
                * 保证金(正常还款可退还)
                <input type="number" id="Deposit"
                    style="height:30px;margin:10px;background-color: azure;width:20%;left: 0%"><br>
                * 服务费
                <input type="number" id="ServiceCharges"
                    style="height:30px;margin:10px;background-color: azure;width:20%;left: 0%"><br>
                * 其它费用
                <input type="number" id="OtherCharges"
                    style="height:30px;margin:10px;background-color: azure;width:20%;left: 0%"><br>
                * 首付款合计
                <input type="number" id="Total"
                    style="height:30px;margin:10px;background-color: azure;width:20%;left: 0%"><br>
                * 月还款
                <input type="number" id="Monthly"
                    style="height:30px;margin:10px;background-color: azure;width:20%;left: 0%"><br>
                <input type="button" value="返回" onclick="Back()"
                    style="position:absolute; height:45px;width: 100px;font-size:30px;left: 25%;">
            </div>
        </div>


        <script>

            var TotalPrice, DownPaymentRatio, ByStages, Service, LoanAmount, DownPaymentAmount, Deposit, ServiceCharges, ServiceCharges, OtherCharges, Total, Monthly;   <!--机器总价，首付比例，分期时间，服务费比例, 贷款额，首付金额，保证金，服务费，其它费用，首付款合计，月还款-->

            function init(){
                
                if(document.getElementById("radio").checked)
                {
                    document.getElementById("page0").style.display = "none";
                    document.getElementById("page1").style.display = "block";
                }
                else{
                    return;
                }
            }
                function Calculator() {
                    TotalPrice = document.getElementById("TotalPrice").value;
                    DownPaymentRatio = document.getElementById("DownPaymentRatio").value;
                    ByStages = document.getElementById("ByStages").value;
                    Service = document.getElementById("Service").value;

                    if (TotalPrice == "") {
                        document.getElementById("TotalPrice").style.backgroundColor = "red";
                        return;
                    }
                    //机器总价
                    Totalprice = parseFloat(TotalPrice);
                    //首付比例
                    DownPaymentRatio = parseFloat(DownPaymentRatio);
                    //贷款月份
                    ByStages = parseFloat(ByStages);
                    //服务费比例
                    Service = parseFloat(Service);
                    //首付款
                    DownPaymentAmount = (Totalprice * DownPaymentRatio) / 100;
                    //贷款额
                    LoanAmount = Totalprice - DownPaymentAmount;
                    //保证金
                    Deposit = LoanAmount * 0.04 + 5000;
                    //服务费
                    ServiceCharges = (Totalprice * Service) / 100;
                    //其它费用
                    OtherCharges = 4000;
                    //首付款合计
                    Total = DownPaymentAmount + Deposit + ServiceCharges + OtherCharges;
                    //月还款
                    Monthly = (LoanAmount + (LoanAmount * 0.51458 * ByStages / 100)) / ByStages + 100;

                    document.getElementById("TotalPrice").style.backgroundColor = "azure";
                    //界面赋值
                    document.getElementById("LoanAmount").value = LoanAmount;
                    document.getElementById("DownPaymentAmount").value = DownPaymentAmount;
                    document.getElementById("Deposit").value = Deposit;
                    document.getElementById("ServiceCharges").value = ServiceCharges;
                    document.getElementById("OtherCharges").value = OtherCharges;
                    document.getElementById("Total").value = Total;
                    document.getElementById("Monthly").value = Monthly;


                    //切换界面
                    document.getElementById("page1").style.display = "none";
                    document.getElementById("page2").style.display = "block";
                }


            function Back() {
                document.getElementById("page2").style.display = "none";
                document.getElementById("page1").style.display = "block";
            }
        </script>
    </body>
</heml>
