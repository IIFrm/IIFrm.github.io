# ex1

## source 
[Interpolants as Classifier](http://theory.stanford.edu/~aiken/publications/papers/cav12a.pdf) by Rahul Sharma, Aditya V. Nori, and Alex Aiken

## program
```c
int ex1(int* a) {
    int x;
    int y;
    int xa = a[0];
    int ya = a[1];
    int loop_times = a[2] % 10;
    int branch = 1;

    iif_assume(xa + 2 * ya >= 0);
    while (loop_times-- > 0) {
        recordi(xa, ya, loop_times);
        x = xa + 2 * ya;
        y = -2 * xa + ya;

        x++;
        if (branch) y = y + x;
        else y = y - x;
        branch = 1 - branch;

        xa = x - 2 * y;
        ya = 2 * x + y;
    }
    recordi(xa, ya, loop_times);
    iif_assert(xa + 2 * ya >= 0);
    return 0;
}
```

##Selective Learning Results:

```
TRY SVM method ...
[1]|-->> SVM: 0.06058642471753994{0}  +  0.0999943031863646{1}  +  0.05940439234788367{2} >= 0.08111111974953818
[2]|-->> SVM: 0.06631895976111879{0}  +  0.1212739560654856{1}  +  0.01789083688462884{2} >= 0.1129110458523937
[3]|-->> SVM: 0.1485900803820508{0}  +  0.2996459568992633{1}  +  -0.1277931908469569{2} >= 0.7146881832552054
[4]|-->> SVM: 0.1485900721371927{0}  +  0.2996459402727316{1}  +  -0.1277931837560643{2} >= 0.7146880881118705
[5]|-->> SVM: 0.3265530804582903{0}  +  0.6596045280729737{1}  +  -0.01140253507250566{2} >= 0.5759553439210094
[6]|-->> SVM: 0.7413939056969667{0}  +  1.477861981026258{1}  +  -0.01618406025729691{2} >= -0.4827934880486282
[7]|-->> SVM: 0.9997274299959287{0}  +  1.999449668182173{1}  +  -1.375305864570464e-05{2} >= -0.9994780002052721
[8]|-->> SVM: 1.999538091566819{0}  +  3.999079223757064{1}  +  0.000148857381773837{2} >= -1.001291332795518
[9]|-->> SVM: 1.999538542662208{0}  +  3.999080130525186{1}  +  0.0001485082398851034{2} >= -1.001289264153456
[10]|-->> SVM: 2.0009995212354{0}  +  4.001999040456738{1}  +  1.221747218949076e-07{2} >= -1.000000690073648
[11]|-->> SVM: 1.999644005263528{0}  +  3.999282697172905{1}  +  4.846798548285847e-06{2} >= -0.9995982325649493
[12]|-->> SVM: 1.999634342638707{0}  +  3.999263227704914{1}  +  1.848351645777901e-05{2} >= -1.000619691331849
[13]|-->> SVM: 1.999634320339169{0}  +  3.999263182772921{1}  +  1.851532393182254e-05{2} >= -1.000619851794909
[14]|-->> SVM: 1.999756873704314{0}  +  3.999519261035232{1}  +  -1.820318122014442e-05{2} >= -0.9993940278072841
[15]|-->> SVM: 1.9997120892765{0}  +  3.999429410676157{1}  +  2.688028548192278e-06{2} >= -0.999487539724214
[16]|-->> SVM: 1.999712073017804{0}  +  3.999429379970422{1}  +  2.647247565157329e-06{2} >= -0.9994871954841074
[17]|-->> SVM: 1.99971235722264{0}  +  3.999429948536515{1}  +  2.500921631509723e-06{2} >= -0.9994865945382116
[18]|-->> SVM: 1.999712098211992{0}  +  3.999429432420426{1}  +  2.578981938117231e-06{2} >= -0.9994867162608898
[19]|-->> SVM: 1.999737061226469{0}  +  3.999479331550923{1}  +  1.362606633303898e-06{2} >= -0.999484540647245
[20]|-->> SVM: 1.999737264650781{0}  +  3.999479735692559{1}  +  1.395296055814801e-06{2} >= -0.9994849420733409
[21]|-->> SVM: 1.999737319442322{0}  +  3.999479840284436{1}  +  1.295410378582469e-06{2} >= -0.9994850416293743
[22]|-->> SVM: 1.999737104426771{0}  +  3.99947941709566{1}  +  1.362382721303845e-06{2} >= -0.9994846253557625
[23]|-->> SVM: 1.999737770518664{0}  +  3.999480750832845{1}  +  1.735040385142383e-06{2} >= -0.9994859606667887
[24]|-->> SVM: 1.999736243562666{0}  +  3.999477658592241{1}  +  -5.802758273887321e-09{2} >= -0.999482830055058
[25]|-->> SVM: 1.999736683978199{0}  +  3.999478559315207{1}  +  7.216234605422756e-07{2} >= -0.9994837506092153
[26]|-->> SVM: 1.999736940534603{0}  +  3.999479071029832{1}  +  8.142563483470866e-07{2} >= -0.9994842609958141
[27]|-->> SVM: 1.999736935189702{0}  +  3.999479058911255{1}  +  7.751786024190466e-07{2} >= -0.9994842475061887
[28]|-->> SVM: 1.999736578829985{0}  +  3.999478352391312{1}  +  7.550495328065288e-07{2} >= -0.9994835471406986
[29]|-->> SVM: 1.999736579516515{0}  +  3.99947835611637{1}  +  8.153738884075779e-07{2} >= -0.9994835532161233
[30]|-->> SVM: 1.999736790685083{0}  +  3.999478769771632{1}  +  6.995844268886664e-07{2} >= -0.9994839581624433
[31]|-->> SVM: 1.999736422886094{0}  +  3.999478040379272{1}  +  6.739274660272354e-07{2} >= -0.9994832349378271
[32]|-->> SVM: 1.999736691406866{0}  +  3.999478577134683{1}  +  8.008879776727484e-07{2} >= -0.9994837714250018
--------------------------------------------------------------------------------------------------------------------
Finish running svm for 32 times.
  Cannot divide by SVM perfectly.
TRY SVM-I method ...
[1]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332880720217497{0}  +  0.2665808408908266{1}  +  2.647607495470661e-05{2} >= -0.9996362195669803 
     |  /\ 0.9996410445949664{0}  +  1.999276566798997{1}  +  -1.651544200198529e-05{2} >= -1.00050269276835 
     |  /\ 1.999341899535921{0}  +  3.998688901764496{1}  +  1.523462723440616e-05{2} >= -1.000525063209352 
     ------------------------------------------------------
[2]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332880881341296{0}  +  0.2665809814653323{1}  +  2.311098627849617e-05{2} >= -0.9996119242378541 
     |  /\ 0.9996413346358963{0}  +  1.999277151343151{1}  +  -1.634676206441199e-05{2} >= -1.000502752583998 
     |  /\ 1.999341858537377{0}  +  3.998688819142529{1}  +  1.529355578355762e-05{2} >= -0.9995509674190544 
     ------------------------------------------------------
[3]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.133291058273177{0}  +  0.2665872220487828{1}  +  2.813651512723059e-06{2} >= -0.9995007043630153 
     |  /\ 0.9996409179939292{0}  +  1.999276311649282{1}  +  -1.655126919697381e-05{2} >= -1.000502780036186 
     |  /\ 1.999360689589196{0}  +  3.998726568660288{1}  +  5.020691276058642e-07{2} >= -0.999483060077182 
     ------------------------------------------------------
[4]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333233216807876{0}  +  0.266644406146452{1}  +  -3.050747896415906e-06{2} >= -0.9997949897414173 
     |  /\ 0.9996414998947216{0}  +  1.999277484403194{1}  +  -1.628759089689069e-05{2} >= -1.000502675844473 
     |  /\ 1.999360653471797{0}  +  3.998726496666592{1}  +  5.053110783137527e-07{2} >= -0.9994830489595188 
     ------------------------------------------------------
[5]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.133328451679201{0}  +  0.2666556708469144{1}  +  6.525496073328529e-06{2} >= -1.000149353133111 
     |  /\ 0.9996409415271899{0}  +  1.999276359077896{1}  +  -1.662643524191765e-05{2} >= -1.000502518341818 
     |  /\ 1.999360645714773{0}  +  3.998726481416583{1}  +  4.929193977432078e-07{2} >= -0.9994829729403136 
     ------------------------------------------------------
[6]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333621124236066{0}  +  0.2667249128551763{1}  +  1.038266564035162e-05{2} >= -1.00005360207507 
     |  /\ 0.9996415416779882{0}  +  1.999277568612598{1}  +  -1.612937980999263e-05{2} >= -1.000503086201206 
     |  /\ 1.999360605816435{0}  +  3.998726402000585{1}  +  4.894880163419657e-07{2} >= -0.9994829212228069 
     ------------------------------------------------------
[7]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333299682759719{0}  +  0.2666606060581175{1}  +  1.071209875497248e-05{2} >= -1.000159342468976 
     |  /\ 0.9996410299013405{0}  +  1.999276537185906{1}  +  -1.667643762592874e-05{2} >= -1.000502232382132 
     |  /\ 1.999360635851644{0}  +  3.998726462236476{1}  +  4.642700588419757e-07{2} >= -0.9994828037306434 
     ------------------------------------------------------
[8]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.133330230087771{0}  +  0.2666620576562466{1}  +  -6.922416392052266e-06{2} >= -0.9998125622639691 
     |  /\ 0.9996409758930156{0}  +  1.999276428338234{1}  +  -1.650789670648578e-05{2} >= -1.000502821072587 
     |  /\ 1.999360645077047{0}  +  3.99872648021281{1}  +  4.888437246108879e-07{2} >= -0.9994829494971782 
     ------------------------------------------------------
[9]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333193899269087{0}  +  0.2666385677718002{1}  +  4.120450639022444e-06{2} >= -1.000024662109013 
     |  /\ 0.9996416942052804{0}  +  1.999277876013679{1}  +  -1.614542263972396e-05{2} >= -1.000502803421114 
     |  /\ 1.999360573914601{0}  +  3.998726338601131{1}  +  4.805644238103923e-07{2} >= -0.9994828450580826 
     ------------------------------------------------------
[10]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333976969537236{0}  +  0.2667903382138076{1}  +  0.000161782196481719{2} >= -1.001152698150008 
     |  /\ 0.9996412779773323{0}  +  1.999277037154286{1}  +  -1.650565522171021e-05{2} >= -1.000502363058331 
     |  /\ 1.999360635169865{0}  +  3.998726460906596{1}  +  4.625460405804915e-07{2} >= -0.9994827935151989 
     ------------------------------------------------------
[11]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332911292194792{0}  +  0.2665874040101195{1}  +  1.325506568616852e-06{2} >= -0.9994907449101902 
     |  /\ 0.9996409197040066{0}  +  1.999276315095827{1}  +  -1.657382438180477e-05{2} >= -1.000502709757711 
     |  /\ 1.999360589628907{0}  +  3.998726370026333{1}  +  4.72924256200713e-07{2} >= -0.9994828148483066 
     ------------------------------------------------------
[12]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333316823871113{0}  +  0.2666635526688544{1}  +  7.25273282248251e-06{2} >= -1.00001022146796 
     |  /\ 0.9996412349935895{0}  +  1.999276950525456{1}  +  -1.634375202108629e-05{2} >= -1.000502914910612 
     |  /\ 1.99936066001095{0}  +  3.998726509649316{1}  +  5.079199993929251e-07{2} >= -0.9994830689392984 
     ------------------------------------------------------
[13]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333319328521227{0}  +  0.2666633881533225{1}  +  6.210673234363639e-06{2} >= -1.000072597785163 
     |  /\ 0.9996412757596431{0}  +  1.999277032684745{1}  +  -1.645773246172766e-05{2} >= -1.000502510250953 
     |  /\ 1.999360708266408{0}  +  3.998726605921689{1}  +  4.984678625419292e-07{2} >= -0.9994830549549079 
     ------------------------------------------------------
[14]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333304039504428{0}  +  0.2666609756890577{1}  +  6.476623490736522e-06{2} >= -1.000009127676606 
     |  /\ 0.9996409933795576{0}  +  1.999276463580486{1}  +  -1.652881910585435e-05{2} >= -1.000502731410961 
     |  /\ 1.999360682906001{0}  +  3.998726555740177{1}  +  4.779664379839232e-07{2} >= -0.9994829190545715 
     ------------------------------------------------------
[15]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333318456043817{0}  +  0.2666600437638303{1}  +  4.863259910503626e-06{2} >= -0.9996559243613774 
     |  /\ 0.9996409525244303{0}  +  1.999276381241501{1}  +  -1.654485054203292e-05{2} >= -1.000502746181155 
     |  /\ 1.999360569134865{0}  +  3.998726329254112{1}  +  4.69896171750861e-07{2} >= -0.9994827811169671 
     ------------------------------------------------------
[16]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333303836976107{0}  +  0.2666599524525169{1}  +  6.400726727695538e-06{2} >= -1.00010709717742 
     |  /\ 0.9996410452514795{0}  +  1.999276568122255{1}  +  -1.668111744601575e-05{2} >= -1.0005021947145 
     |  /\ 1.99936058721056{0}  +  3.998726365311597{1}  +  4.666475916792479e-07{2} >= -0.9994827775662998 
     ------------------------------------------------------
[17]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332910572461263{0}  +  0.2665871153534581{1}  +  6.009060257494703e-06{2} >= -0.9995239501204765 
     |  /\ 0.9996409931146104{0}  +  1.999276463046428{1}  +  -1.663273259522313e-05{2} >= -1.000502420094563 
     |  /\ 1.99936056234236{0}  +  3.998726315613794{1}  +  4.766780321574515e-07{2} >= -0.9994828137860168 
     ------------------------------------------------------
[18]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332910991199765{0}  +  0.2665873598286715{1}  +  9.498441858601936e-07{2} >= -0.9994876405049808 
     |  /\ 0.9996417402323914{0}  +  1.999278347360843{1}  +  -1.026619985777799e-05{2} >= -1.000482511793962 
     |  /\ 1.999360581539747{0}  +  3.998726353830477{1}  +  4.78041897622461e-07{2} >= -0.999482837098185 
     ------------------------------------------------------
[19]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332910953357749{0}  +  0.2665873600598131{1}  +  7.261488029763896e-07{2} >= -0.9994859657688266 
     |  /\ 0.9996409775992845{0}  +  1.999276431777076{1}  +  -1.656307181407968e-05{2} >= -1.000502652947034 
     |  /\ 1.999360688654804{0}  +  3.998726567001654{1}  +  4.89607458575847e-07{2} >= -0.9994829892530106 
     ------------------------------------------------------
[20]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333273841503215{0}  +  0.2666544924565455{1}  +  7.739201580814203e-06{2} >= -1.000058541216049 
     |  /\ 0.9996409939062119{0}  +  1.999276464641738{1}  +  -1.672142169839574e-05{2} >= -1.000502152804984 
     |  /\ 1.999360651394454{0}  +  3.998726492446878{1}  +  5.103216551560763e-07{2} >= -0.9994830754585564 
     ------------------------------------------------------
[21]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333296720550652{0}  +  0.2666583959614435{1}  +  5.72561706546626e-06{2} >= -1.000117717336991 
     |  /\ 0.9996409469812022{0}  +  1.999276370069822{1}  +  -1.662085081743925e-05{2} >= -1.000502526701894 
     |  /\ 1.999360308459359{0}  +  3.998725809934001{1}  +  4.753171154447955e-07{2} >= -0.9994825997127919 
     ------------------------------------------------------
[22]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333344517015858{0}  +  0.2666690688952543{1}  +  6.387994400725017e-06{2} >= -1.000009002769218 
     |  /\ 0.9996409279880538{0}  +  1.999276331791435{1}  +  -1.659845544699223e-05{2} >= -1.000502623101056 
     |  /\ 1.999360626455143{0}  +  3.99872644324418{1}  +  4.812523499708732e-07{2} >= -0.9994828916242113 
     ------------------------------------------------------
[23]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333349535949304{0}  +  0.2666694608701845{1}  +  6.029415322073017e-06{2} >= -1.000068749628838 
     |  /\ 0.9996409803597714{0}  +  1.999276437340413{1}  +  -1.665797477512498e-05{2} >= -1.000502363989654 
     |  /\ 1.999371863114391{0}  +  3.998748751471936{1}  +  5.015985230727438e-06{2} >= -0.999517539574299 
     ------------------------------------------------------
[24]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333322353243043{0}  +  0.2666644571847163{1}  +  1.319461372384367e-06{2} >= -1.000006624234629 
     |  /\ 0.9996408965759542{0}  +  1.999276268483698{1}  +  -1.658004112004008e-05{2} >= -1.000502726688865 
     |  /\ 1.999371871922563{0}  +  3.998748768866363{1}  +  5.025267569180869e-06{2} >= -0.9995175989606651 
     ------------------------------------------------------
[25]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332908906452401{0}  +  0.2665863985375605{1}  +  1.833404438739139e-05{2} >= -0.9996116114696747 
     |  /\ 0.9996409688486096{0}  +  1.999276414141164{1}  +  -1.663210882751898e-05{2} >= -1.000502459290146 
     |  /\ 1.999368734292261{0}  +  3.998742519587324{1}  +  4.996171988125298e-06{2} >= -0.9995148844318464 
     ------------------------------------------------------
[26]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333390297442476{0}  +  0.2666780654014291{1}  +  3.626599663353325e-07{2} >= -1.000003194955468 
     |  /\ 0.999640910520867{0}  +  1.999276296588064{1}  +  -1.656368051428103e-05{2} >= -1.000502754315676 
     |  /\ 1.999371870784501{0}  +  3.998748767302999{1}  +  4.982005506803944e-06{2} >= -0.9995173546485603 
     ------------------------------------------------------
[27]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333277227975525{0}  +  0.2666555018863073{1}  +  3.452526993796834e-06{2} >= -1.000008180988061 
     |  /\ 0.9996409378319981{0}  +  1.99927635163057{1}  +  -1.654650339455443e-05{2} >= -1.000502763818076 
     |  /\ 1.999371881365278{0}  +  3.998748789353328{1}  +  4.922032800891429e-06{2} >= -0.9995170259353472 
     ------------------------------------------------------
[28]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1332933743509714{0}  +  0.2665910237965519{1}  +  1.945579828560584e-05{2} >= -0.9996503137323884 
     |  /\ 0.9995583133499508{0}  +  1.999114754298532{1}  +  -9.986136388917544e-07{2} >= -1.000184244287084 
     |  /\ 1.999368716477932{0}  +  3.998742483751641{1}  +  5.017810558172187e-06{2} >= -0.999514991621254 
     ------------------------------------------------------
[29]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.133331803745389{0}  +  0.2666635881830622{1}  +  1.261437423683009e-06{2} >= -1.000006976521263 
     |  /\ 0.9996449272148027{0}  +  1.999284174621394{1}  +  -1.699703660040797e-05{2} >= -1.00051698970492 
     |  /\ 1.999371870131938{0}  +  3.998748766293545{1}  +  4.96412459227713e-06{2} >= -0.9995172535564052 
     ------------------------------------------------------
[30]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.133330217988797{0}  +  0.2666600725937842{1}  +  1.01747467325386e-05{2} >= -1.000077037368101 
     |  /\ 0.9996449986043672{0}  +  1.999284320873741{1}  +  -1.691377357815327e-05{2} >= -1.000516892156156 
     |  /\ 1.999375846823284{0}  +  3.998756745481501{1}  +  1.388733295470956e-06{2} >= -0.9995003714429913 
     ------------------------------------------------------
[31]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333230951954574{0}  +  0.2666476831760579{1}  +  3.317300317895455e-05{2} >= -0.9999834134983416 
     |  /\ 0.999558849029512{0}  +  1.999115849301475{1}  +  -9.860040455222929e-07{2} >= -1.000181917741429 
     |  /\ 1.999375846778435{0}  +  3.998756745132255{1}  +  1.404748438460501e-06{2} >= -0.999500461446587 
     ------------------------------------------------------
[32]|-->> SVM-I:  
     ------------------------------------------------------ 
     |     0.1333354543444802{0}  +  0.2666709577395708{1}  +  2.060125551428538e-06{2} >= -1.000003335441363 
     |  /\ 0.9996537676938146{0}  +  1.999302331836844{1}  +  -5.105459770504694e-06{2} >= -1.000499933237734 
     |  /\ 1.999375848467366{0}  +  3.998756748756477{1}  +  1.388729785389842e-06{2} >= -0.9995003727235598 
     ------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------
Finish running svm_i for 32 times.
  Cannot divide by SVM_I perfectly.
```