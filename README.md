# 粤难粤说APP
[40x40秒的带narration 语音口白的Powerpoint](https://gitee.com/NFUNM101/final_project/blob/master/%E7%B2%A4%E9%9A%BE%E7%B2%A4%E8%AF%B4APP.pptx)  

发布日期|2019-12-23
--|:--:|
项目名称|粤难粤说
项目状态|进行中
项目主人|张美玲
项目的开发者|张美玲
项目的测试者|张美玲 

## 一、价值主张设计

#### 背景概述
广东是个神奇的地方，它有着好听的地方方言——粤语，有着两个一线城市——深圳和广州，有着非常会做生意的广东人，有着好吃的广东美食。这些的种种吸引着许多人来广东定居或者游玩，但对于这些人来说，广东又是个难懂的地方，问题来了，他们听不懂粤语。如今市面上的粤语app主要用于学习，但日常交流的“翻译器”也是人们所需的。
#### 加值宣言
该产品是一款交流与学习的功能相结合的产品，主要使用了语音识别技术，通过语音识别技术，令用户既能在日常中交流无阻，又能令用户在交流的过程中学习粤语。
- 交流无阻 用户因工作原因或游玩来到广东，碰到听不懂粤语的情况，使用语音输入，将粤语输入APP中，APP智能反馈文字或语音翻译，做到不用学会粤语也能交流无阻。
- 学习粤语 用户在广东长期定居，需要学习粤语不再想依赖翻译器，通过APP随时随地学粤语。

#### 核心价值（最小可用产品）--痛点
不会粤语的非广东人遇到只会说粤语的广东人时，出现交流障碍，通过APP进行即时翻译，打破方言阻碍。

#### 人工智能概率性
在语音输入时，反馈的信息内容会受当下的语音环境影响，如语音声音太小，环境太嘈杂，用户咬字不清等情况，但APP可根据句意自动纠错、自动断句添加标点等，当输入的语音信息不清楚时，将会智能识别并给出正确的翻译。

#### 需求列表
功能|用户使用场景|重要程度
--|:--:|--
翻译|当不会粤语的外地人遇到老一辈的广东人，普通话讲不标准，为了能流畅交流，让这个老一辈的广东人讲粤语，通过语音输入，反馈翻译的文字或语音，双方都不影响交流|重要
学习粤语|用户刚开始学习粤语，想与广东人用粤语进行交流，又怕讲不标准，可将APP当作学习工具，语音输入一句想讲的粤语，APP智能修改病句及纠正发音，不用害怕讲不标准闹笑话|次重要

## 二、原型设计
[产品原型——点击此处进入](http://nfunm101.gitee.io/yue_produce)
### 界面/交互设计
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/003548_7b7fcaa7_1648162.png "翻译.PNG")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/003624_e7cb577a_1648162.png "学习.PNG")![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/003641_bea220ad_1648162.png "上传-粤.PNG")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/003921_96bb7fb2_1648162.png "TVB剧.PNG")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/003942_57476318_1648162.png "我的.PNG")
### 信息设计
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/005712_6eb5253b_1648162.png "信息输出.PNG")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/005726_d55e4058_1648162.png "信息学习.PNG")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/005740_8c27c150_1648162.png "信息我的.PNG")

### 产品架构图

#### 产品架构图
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/012406_3993a1a2_1648162.png "粤产品架构图.PNG")
#### 产品功能结构图
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/012600_040dbbf8_1648162.png "粤产品功能架构图.PNG")
#### 产品信息架构图
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/012449_5a585fad_1648162.png "粤产品信息架构图.PNG")
#### 产品流程图
![输入图片说明](https://images.gitee.com/uploads/images/2020/0107/012504_cfbe31c9_1648162.png "粤流程图.PNG")
## 三、API展示
#### API使用与输出
1、百度语音识别api  

- 接口描述：该请求用于语音识别。即输入语音，输出该语音的文字或语音（粤语/普通话）信息。
- 接口地址：http://vop.baidu.com/server_api
- 输入
```  
import sys
import json
import base64
import time

IS_PY3 = sys.version_info.major == 3

if IS_PY3:
    from urllib.request import urlopen
    from urllib.request import Request
    from urllib.error import URLError
    from urllib.parse import urlencode
    timer = time.perf_counter
else:
    from urllib2 import urlopen
    from urllib2 import Request
    from urllib2 import URLError
    from urllib import urlencode
    if sys.platform == "win32":
        timer = time.clock
    else:
        # On most other platforms the best timer is time.time()
        timer = time.time

API_KEY = 'IEWxeETG7ZP5gkxfXM4FVdbo'
SECRET_KEY = 'eMwmXjPsYZUDuyzITFu0BQbXypBwrabZ'

# 需要识别的文件
AUDIO_FILE = './luyin.m4a'  # 只支持 pcm/wav/amr 格式，极速版额外支持m4a 格式
# 文件格式
FORMAT = AUDIO_FILE[-3:]  # 文件后缀只支持 pcm/wav/amr 格式，极速版额外支持m4a 格式

CUID = '123456PYTHON'
# 采样率
RATE = 16000  # 固定值

# 普通版

DEV_PID = 1637  # 1537 表示识别普通话，使用输入法模型。1536表示识别普通话，使用搜索模型。根据文档填写PID，选择语言及识别模型
ASR_URL = 'http://vop.baidu.com/server_api'
SCOPE = 'audio_voice_assistant_get'  # 有此scope表示有asr能力，没有请在网页里勾选，非常旧的应用可能没有

#测试自训练平台需要打开以下信息， 自训练平台模型上线后，您会看见 第二步：“”获取专属模型参数pid:8001，modelid:1234”，按照这个信息获取 dev_pid=8001，lm_id=1234
# DEV_PID = 8001 ;   
# LM_ID = 1234 ;

# 极速版 打开注释的话请填写自己申请的appkey appSecret ，并在网页中开通极速版（开通后可能会收费）

# DEV_PID = 80001
# ASR_URL = 'http://vop.baidu.com/pro_api'
# SCOPE = 'brain_enhanced_asr'  # 有此scope表示有极速版能力，没有请在网页里开通极速版

# 忽略scope检查，非常旧的应用可能没有
# SCOPE = False

class DemoError(Exception):
    pass


"""  TOKEN start """

TOKEN_URL = 'http://openapi.baidu.com/oauth/2.0/token'


def fetch_token():
    params = {'grant_type': 'client_credentials',
              'client_id': API_KEY,
              'client_secret': SECRET_KEY}
    post_data = urlencode(params)
    if (IS_PY3):
        post_data = post_data.encode( 'utf-8')
    req = Request(TOKEN_URL, post_data)
    try:
        f = urlopen(req)
        result_str = f.read()
    except URLError as err:
        print('token http response http code : ' + str(err.code))
        result_str = err.read()
    if (IS_PY3):
        result_str =  result_str.decode()

    print(result_str)
    result = json.loads(result_str)
    print(result)
    if ('access_token' in result.keys() and 'scope' in result.keys()):
        print(SCOPE)
        if SCOPE and (not SCOPE in result['scope'].split(' ')):  # SCOPE = False 忽略检查
            raise DemoError('scope is not correct')
        print('SUCCESS WITH TOKEN: %s  EXPIRES IN SECONDS: %s' % (result['access_token'], result['expires_in']))
        return result['access_token']
    else:
        raise DemoError('MAYBE API_KEY or SECRET_KEY not correct: access_token or scope not found in token response')

"""  TOKEN end """

if __name__ == '__main__':
    token = fetch_token()

    speech_data = []
    with open(AUDIO_FILE, 'rb') as speech_file:
        speech_data = speech_file.read()

    length = len(speech_data)
    if length == 0:
        raise DemoError('file %s length read 0 bytes' % AUDIO_FILE)
    speech = base64.b64encode(speech_data)
    if (IS_PY3):
        speech = str(speech, 'utf-8')
    params = {'dev_pid': DEV_PID,
             #"lm_id" : LM_ID,    #测试自训练平台开启此项
              'format': FORMAT,
              'rate': RATE,
              'token': token,
              'cuid': CUID,
              'channel': 1,
              'speech': speech,
              'len': length
              }
    post_data = json.dumps(params, sort_keys=False)
    # print post_data
    req = Request(ASR_URL, post_data.encode('utf-8'))
    req.add_header('Content-Type', 'application/json')
    try:
        begin = timer()
        f = urlopen(req)
        result_str = f.read()
        print ("Request time cost %f" % (timer() - begin))
    except URLError as err:
        print('asr http response http code : ' + str(err.code))
        result_str = err.read()

    if (IS_PY3):
        result_str = str(result_str, 'utf-8')
    print(result_str)
    with open("result.txt","w") as of:
        of.write(result_str)
```
- 输出
```
{"access_token":"24.5dabb257c9097c30aea2caa9748ab63f.2592000.1579784749.282335-17537195","session_key":"9mzdDtbSM2ybtYJW4kdB3g3KbSXHoKZTBJXfNuiIWacLfX50YPfhW1PTIct+xNJsPGk+LFv+PpUCQWEx3i08Yn0+uf8boA==","scope":"audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test\u6743\u9650 vis-classify_flower lpq_\u5f00\u653e cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_\u5f00\u653eScope vis-ocr_\u865a\u62df\u4eba\u7269\u52a9\u7406 idl-video_\u865a\u62df\u4eba\u7269\u52a9\u7406","refresh_token":"25.f757c46128f7f3ec8093d00758a372e0.315360000.1892552749.282335-17537195","session_secret":"6f94bf1a5a5f77a85a398f1793e37803","expires_in":2592000}

{'access_token': '24.5dabb257c9097c30aea2caa9748ab63f.2592000.1579784749.282335-17537195', 'session_key': '9mzdDtbSM2ybtYJW4kdB3g3KbSXHoKZTBJXfNuiIWacLfX50YPfhW1PTIct+xNJsPGk+LFv+PpUCQWEx3i08Yn0+uf8boA==', 'scope': 'audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test权限 vis-classify_flower lpq_开放 cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_开放Scope vis-ocr_虚拟人物助理 idl-video_虚拟人物助理', 'refresh_token': '25.f757c46128f7f3ec8093d00758a372e0.315360000.1892552749.282335-17537195', 'session_secret': '6f94bf1a5a5f77a85a398f1793e37803', 'expires_in': 2592000}
audio_voice_assistant_get
SUCCESS WITH TOKEN: 24.5dabb257c9097c30aea2caa9748ab63f.2592000.1579784749.282335-17537195  EXPIRES IN SECONDS: 2592000
Request time cost 0.114846
{"err_msg":"audio trans failed","err_no":3316,"sn":"558407106251577192749"}
```  
2、语音合成

- 接口描述：该请求用于语音合成。即上传文本文件或输入文字，输出该文本的文字或语音（粤语/普通话）信息。
- 接口地址：http://tsn.baidu.com/text2audio
- 输入
```
import sys
import json

IS_PY3 = sys.version_info.major == 3
if IS_PY3:
    from urllib.request import urlopen
    from urllib.request import Request
    from urllib.error import URLError
    from urllib.parse import urlencode
    from urllib.parse import quote_plus
else:
    import urllib2
    from urllib import quote_plus
    from urllib2 import urlopen
    from urllib2 import Request
    from urllib2 import URLError
    from urllib import urlencode

APP_ID = '17537195'
API_KEY = 'IEWxeETG7ZP5gkxfXM4FVdbo'

TEXT = "作业好多我好开心"

# 发音人选择, 基础音库：0为度小美，1为度小宇，3为度逍遥，4为度丫丫，
# 精品音库：5为度小娇，103为度米朵，106为度博文，110为度小童，111为度小萌，默认为度小美 
PER = 4
# 语速，取值0-15，默认为5中语速
SPD = 5
# 音调，取值0-15，默认为5中语调
PIT = 5
# 音量，取值0-9，默认为5中音量
VOL = 5
# 下载的文件格式, 3：mp3(default) 4： pcm-16k 5： pcm-8k 6. wav
AUE = 3

FORMATS = {3: "mp3", 4: "pcm", 5: "pcm", 6: "wav"}
FORMAT = FORMATS[AUE]

CUID = "123456PYTHON"

TTS_URL = 'http://tsn.baidu.com/text2audio'


class DemoError(Exception):
    pass


"""  TOKEN start """

TOKEN_URL = 'http://openapi.baidu.com/oauth/2.0/token'
SCOPE = 'audio_tts_post'  # 有此scope表示有tts能力，没有请在网页里勾选


def fetch_token():
    print("fetch token begin")
    params = {'grant_type': 'client_credentials',
              'client_id': API_KEY,
              'client_secret': SECRET_KEY}
    post_data = urlencode(params)
    if (IS_PY3):
        post_data = post_data.encode('utf-8')
    req = Request(TOKEN_URL, post_data)
    try:
        f = urlopen(req, timeout=5)
        result_str = f.read()
    except URLError as err:
        print('token http response http code : ' + str(err.code))
        result_str = err.read()
    if (IS_PY3):
        result_str = result_str.decode()

    print(result_str)
    result = json.loads(result_str)
    print(result)
    if ('access_token' in result.keys() and 'scope' in result.keys()):
        if not SCOPE in result['scope'].split(' '):
            raise DemoError('scope is not correct')
        print('SUCCESS WITH TOKEN: %s ; EXPIRES IN SECONDS: %s' % (result['access_token'], result['expires_in']))
        return result['access_token']
    else:
        raise DemoError('MAYBE API_KEY or SECRET_KEY not correct: access_token or scope not found in token response')


"""  TOKEN end """

if __name__ == '__main__':
    token = fetch_token()
    tex = quote_plus(TEXT)  # 此处TEXT需要两次urlencode
    print(tex)
    params = {'tok': token, 'tex': tex, 'per': PER, 'spd': SPD, 'pit': PIT, 'vol': VOL, 'aue': AUE, 'cuid': CUID,
              'lan': 'zh', 'ctp': 1}  # lan ctp 固定参数

    data = urlencode(params)
    print('test on Web Browser' + TTS_URL + '?' + data)

    req = Request(TTS_URL, data.encode('utf-8'))
    has_error = False
    try:
        f = urlopen(req)
        result_str = f.read()

        headers = dict((name.lower(), value) for name, value in f.headers.items())

        has_error = ('content-type' not in headers.keys() or headers['content-type'].find('audio/') < 0)
    except  URLError as err:
        print('asr http response http code : ' + str(err.code))
        result_str = err.read()
        has_error = True

    save_file = "error.txt" if has_error else 'result.' + FORMAT
    with open(save_file, 'wb') as of:
        of.write(result_str)

    if has_error:
        if (IS_PY3):
            result_str = str(result_str, 'utf-8')
        print("tts api  error:" + result_str)

    print("result saved as :" + save_file)
```
- 输出
```
fetch token begin
{"access_token":"24.e64058ba1ed4ead39d6f245d5d593457.2592000.1579784867.282335-17537195","session_key":"9mzdXvNzuOQwnUZMt42nMIxHa3K7+L8OGSNdaiI6852guxyBRlbAfUIUslatsnTrCdM1tKAVeDKlu3E6PzA+CQDJ1uscCA==","scope":"audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test\u6743\u9650 vis-classify_flower lpq_\u5f00\u653e cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_\u5f00\u653eScope vis-ocr_\u865a\u62df\u4eba\u7269\u52a9\u7406 idl-video_\u865a\u62df\u4eba\u7269\u52a9\u7406","refresh_token":"25.04aa8a8bed93e026c3f4444a4934f9d0.315360000.1892552867.282335-17537195","session_secret":"46628ed024217dbbb9b1ce9d5aadf84e","expires_in":2592000}

{'access_token': '24.e64058ba1ed4ead39d6f245d5d593457.2592000.1579784867.282335-17537195', 'session_key': '9mzdXvNzuOQwnUZMt42nMIxHa3K7+L8OGSNdaiI6852guxyBRlbAfUIUslatsnTrCdM1tKAVeDKlu3E6PzA+CQDJ1uscCA==', 'scope': 'audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test权限 vis-classify_flower lpq_开放 cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_开放Scope vis-ocr_虚拟人物助理 idl-video_虚拟人物助理', 'refresh_token': '25.04aa8a8bed93e026c3f4444a4934f9d0.315360000.1892552867.282335-17537195', 'session_secret': '46628ed024217dbbb9b1ce9d5aadf84e', 'expires_in': 2592000}
SUCCESS WITH TOKEN: 24.e64058ba1ed4ead39d6f245d5d593457.2592000.1579784867.282335-17537195 ; EXPIRES IN SECONDS: 2592000
%E4%BD%9C%E4%B8%9A%E5%A5%BD%E5%A4%9A%E6%88%91%E5%A5%BD%E5%BC%80%E5%BF%83
test on Web Browserhttp://tsn.baidu.com/text2audio?tok=24.e64058ba1ed4ead39d6f245d5d593457.2592000.1579784867.282335-17537195&tex=%25E4%25BD%259C%25E4%25B8%259A%25E5%25A5%25BD%25E5%25A4%259A%25E6%2588%2591%25E5%25A5%25BD%25E5%25BC%2580%25E5%25BF%2583&per=4&spd=5&pit=5&vol=5&aue=3&cuid=123456PYTHON&lan=zh&ctp=1
result saved as :result.mp3
```  
#### 使用后风险报告
- > **百度语音识别API错误率评估**  
百度研发出了基于多层单向LSTM（长短时记忆模型）的汉语声韵母整体建模技术，并成功把连接时序分类（CTC）训练技术嵌入到语音识别传统技术建模框架中。该技术能够使机器的语音识别相对错误率降低15%，使汉语安静环境普通话语音识别的准确率接近97%。[点击此处阅读原文](http://news.zol.com.cn/549/5499324.html)
- 可能出现的错误  
1. 粤语语音输入**luoyou**（屁股的意思），输出普通话的结果为**柚子**(粤语柚子的发音为“luyou”）
2. 上传文本一键翻译，遇上生僻字**叅**无法准确翻译
3. 用户选择粤语翻译普通话，在语音输入时输入了普通话，选择错误，系统自动将输入的普通话翻译成了普通话

- 产品定价
![输入图片说明](https://images.gitee.com/uploads/images/2019/1224/223329_1af6f36e_1648162.png "费用.PNG")

## 一句话版本
一键让你变成广东人

## 一分钟版本
粤语因发音好听等原因被人所喜爱，广东经济一直都位居前列，因此许多人会选择来广东工作，在广东长居需要懂得一点粤语才能真正体会到广东的风土人情，这款APP就为在广东长居的非广东人提供了学习粤语的机会，本产品的核心功能为翻译器，可实时获得翻译内容，普通话与粤语相互转化。除此之外，还有提供学习的功能，如看剧，纠正发音，听粤语歌等。主要使用到的API有语音识别功能，通过语音输入获得翻译。
