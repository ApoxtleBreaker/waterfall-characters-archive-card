
==项目背景==
此项目目前仅用html css js完成 主要是为了练习前端开发能力和兴趣指导
发出来共享一下开发成果 也是记录一下自己的编写历程
因为是高中生  更新时间不一定充足 
仅仅在本地环境制作和运行  部署在服务器环境可能需要额外配置调试
项目为一个展示自己喜欢的动漫角色的流动照片墙
对每一个角色也可以打开窗口查看详细信息


==目前问题==
虽然不影响观感 但是在打开小窗的时候切换角色控制台会莫名报错
cover元素的style为null
!尝试把element.style改成window.getComputedStyle(element)
!!名称切换功能未完成  测试json导入jp_roma字段显示有误
!!readJSON函数传入参数自动加上.json后缀   传入参数不能包含后缀  调试中如果需要可以把+'.json'去掉 然后传入文件名

==计划==
1.加入文件自动生成json的文件和填入后自动生成的文件
(一个是空白的只需要你填就行 看不见效果也不用到编辑器中修改  一个是页面上 你去改元素值 看着差不多了直接生成)
几个input输入角色相关信息
最后输出直接是完整的json语句/文件
2.加入点开窗口后背景不可互动的效果 预计用一个div实现
3.加入名称切换
4.加入动画
5.背景图用json导入 不用直接在html中写路径 改用读取json
6.打开角色播放对应的音乐+台词
    如果可能 设想一下加入动画切片 时间成本较高
    用卡片翻转效果 展示在卡片背面
7.加入设置页面  调整部分可选择效果 用函数()在控制台执行打开设置页面
    在设置页面藏一个我自己的个人档案  加入信号干扰的效果在图片上

=用户视角=
应该简单的流动照片页面
图片是我自己喜欢的动漫角色
鼠标悬浮到图片上切换到另一张图片
左键打开档案页面
档案页面右上角有一个小小的关闭按钮
档案左上角的图片可以切换
   左键单击切换封面时的另一张图
   左键双击切换大图立绘

=开发者视角=
    ==基础数据更改==
    在img文件夹中使用 文件名-1.webp 文件名-2 文件名-portrait.webp来设置一个新角色的图片
        -1为初始图 -2为切换图 -portrait为立绘图 
        e.g. FutabaRio-1.webp FutabaRio-2.webp FutabaRio-portrait.webp
    在json文件夹中添加文件来增加新角色的档案信息
        文件名为 文件名.json 需要与img文件中对应
        e.g. FutabaRio.json
        以下是json文件的格式  也可以直接去json文件夹中的文件查看/更改
        {
            "name": {
                "name_cn": "双叶理央",
                "name_jp": "双葉理央",
                "name_jp_2": "ふたば りお",
                "name_en": "Futaba Rio"
            },
            "information": "<p>轻小说《青春猪头少年系列》及衍生作品中的角色,由种崎敦美配音。</p><p>在17岁，10月23日出生，身高155厘米，灰色长卷发，身着白大褂，体型较小，戴着眼镜，披在制服外面的白袍特别显眼，挺直背脊的身影挺帅气。</p><p>身材很好，在初中时因为被同班男生讨论而十分厌恶自己的身体，对此很自卑。</p><p>是个冷静沉着的理科女，神奈川县立峰原高中二年级生，参加社员只有一名的科学社，性格孤僻自卑。在学校里被当作怪人。</p>",
            "tags": [
                "[+]INTP",
                "[+]实验服",
                "[+]理科女",
                "[-]巨乳"
            ]
        }
        json文件的修改可能不是一次就能成功的  因为信息长度等原因
    如果需要更改照片墙上的图片 只要在html文件中把row-item中的img的src属性改成新的图片文件名即可
    名称需要和前面说的img json一致
    原则上名字可以随便取 只要统一 但是为了防止不必要的bug和提高可辨识性 建议把图片名改成你对应那个角色的英语名/日语罗马音等诸如此类的纯英字节
        ==项目文件说明
    文件中的index为主要文件（包含开发过程中的注释和调试痕迹）
    如果你需要写入你的角色 为了方便你观察效果和制作 我准备了一个display-orginal.html文件
    在里面有细致的指引 简单更改文字部分就可以让你直观看到窗口中档案的变化
    index-light.html把多余的部分删除 文件更小一点 如果不需要更改源码可以使用这一个
    
    ==代码讲解==
        页面上的主要部分为6个row的div显示
        滚动效果是css定义的@keyframes
        对于每一行的滚动速度都设置了不同的变量在:root中 可以方便的更改流速
        往下滚动后第二个衔接上的同样的row-item是在js里生成的
        在执行之初 就会把本来row中的row-item复制一份到下方以完成衔接
        
        没有学习过组件化开发 所以窗口就是直接写的单独的函数
        窗口的背景为filter:blur 实现毛玻璃效果
        但是此属性对于部分浏览器可能不支持 
        在窗口中大量元素以绝对定位的方式出现
        标签中的[+] [-]仅为装饰 无实义 只是作者来区分这个角色让自己喜欢/不太喜欢的点(当然是个人观点)

==相关语言
HTML HTML5 CSS CSS3 JavaScript JSON


=======================
===translated by Google:

== Project background ==
This project is currently completed using HTML, CSS, and JavaScript. It is mainly for practicing front-end development skills and interest guidance. I shared it to share the development results and record my own writing process. Since it is a high school student, the update time is not necessarily complete. It is only developed and run locally, and the deployment on the server environment may require additional configuration and debugging. The project is a wall of moving pictures of favorite anime characters. Each character can also open a detailed window to view information.

== Current problems ==
Although it does not affect the visual, when opening the small window, the console will report an error when switching characters. The style of the cover element is null. I tried to change element.style to window.getComputedStyle(element). However, the name switching function has not been completed. The test of importing the jp_roma field displays incorrectly. The readJSON function automatically adds the.json suffix to the parameter, and the parameter cannot contain the suffix. Debugging is underway if you need to remove the + '.json' suffix and pass in the file name.

== Plan ==
1. Add files for automatic generation of json and files to be filled in automatically generated files
(One is a blank one, you only need to fill in and it will not be visible, and you do not need to modify it in the editor. The other is on the page, you go to the element value and see it is close to completion, and you can directly generate it)
Several input fields for character-related information are provided.
The final output is a complete json statement or file.
2. Add the effect of background interactivity when opening a window. It is expected to use a div.
3. Add name switching.
4. Add animation.
5. Background images are imported from json, not directly written in the html file.
6. Open the character and play the corresponding music and dialogue.
    If possible, consider adding animation slicing, which is time-consuming.
    Use card flipping effect to show the card behind the picture.
7. Add a settings page to adjust some selectable effects. Use a function () in the console to open the settings page.
    Hide a personal profile on the settings page and add signal interference effects on the picture.
= User perspective =
It should be a simple moving picture page.
The pictures are my favorite anime characters.
When the mouse hovers over the picture, it switches to the next picture.
The left button opens the character profile page.
The character profile page has a small close button in the upper right corner.
The upper left image can switch between the cover image and the full-body portrait.
   Left-clicking switches to the other image during the cover switch.
   Left-clicking twice switches to the full-body portrait.

= Developer perspective =
    == Basic data change ==
    In the img folder, use the file name -1.webp, file name -2, and file name -portrait.webp to set a new character's picture.
        -1 is the initial picture, -2 is the switch picture, and -portrait is the portrait picture.
        e.g. FutabaRio-1.webp FutabaRio-2.webp FutabaRio-portrait.webp
    In the json folder, add a file to increase the information of the new character.
        The file name is the file name.json, which should correspond to the img file.
        e.g. FutabaRio.json
        The following is the format of the json file. You can also check or modify the files in the json folder directly.
        {
            "name": {
                "name_cn": "双叶理央",
                "name_jp": "双葉理央",
                "name_jp_2": "ふたば りお",
                "name_en": "Futaba Rio"
            },
            "information": "<p>《青春猪头少年系列》及衍生作品中的角色,由种崎敦美配音。</p><p>17岁,10月23日出生,身高155厘米,灰色长卷发,身着白大褂,体型较小,戴着眼镜,披在制服外面的白袍特别显眼,挺直背脊的身影挺帅气。</p><p>身材很好,在初中时因为被同班男生讨论而十分厌恶自己的身体,对此很自卑。</p><p>是个冷静沉着的理科女,神奈川县立峰原高中二年级生,参加社员只有一名的科学社,性格孤僻自卑。在学校里被当作怪人。</p>",
            "tags": [
                "[+]INTP",
                "[+]实验服",
                "[+]理科女",
                "[-]巨乳"
            ]
        }
        The modification of the json file may not be successful all at once because of the length of the information.
    If you need to change the pictures on the wall, you can simply change the src attribute of the img in the row-item in the html file.
    The name should be consistent with the img json. It is recommended to use a pure English name or a Japanese romanization of the character's name to make it easier to identify.
        == Project file description ==
    The index file is the main file (with comments and debugging traces in the development process).
    If you need to write your character, to facilitate your observation and creation, I prepared a display-orginal.html file.
    In it, there are detailed instructions and simple modifications can let you see the changes in the character profile in real time.
    index-light.html deletes unnecessary parts and makes the file smaller. If you do not need to modify the source code, you can use this one.
    
    == Code explanation ==
        The main part of the page is a 6-row div display.
        The scroll effect is defined by CSS @keyframes.
        For each row's scroll speed, different variables are set in :root, which can be easily changed.
        After scrolling down, the second row-item that is connected to the same row is generated in js.
        At the beginning, all the row-item in the row will be copied down to complete the connection.
        
        I have not learned component development yet, so the window is written separately.
        However, this attribute may not be supported by some browsers.
        In the window, a large number of elements appear in absolute positioning.
        The [+] [-] tags are decorative and have no intrinsic meaning, but are used by the author to distinguish this character as one that he likes or dislikes (of course, it is a personal opinion).


== Related languages ==
HTML HTML5 CSS CSS3 JavaScript JSON
===

==================
作者的联系方式[How to contact me]
QQ: 1215582857
邮箱[Email]: ystsfankui@hotmail.com
BiliBili: https://space.bilibili.com/1979641484
我只是个废物高二学生 所以我也留一下我的steam 欢迎找我玩
I'm just a silly Chinese senior high school student in senior 2 (2024-2025) , so i also public my Steam, welcome to play with me
Steam: https://steamcommunity.com/id/ApoxtleNeverDie
