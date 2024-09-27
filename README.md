 >!:我希望我能把这个项目做完 在学校和家里的压力下
# = =项目背景= =
项目为一个展示自己喜欢的动漫角色的流动照片墙,对每一个角色也可以打开窗口查看详细信息
此项目目前**仅用html css js**完成 主要是为了练习前端开发能力和兴趣指导
发出来共享一下开发成果 也是记录一下自己的编写历程
因为是**高中生**  更新时间不一定充足 
仅仅在本地环境制作和运行  部署在服务器环境可能需要额外配置调试

# =用户视角=
应该简单的流动照片页面
图片是我自己喜欢的动漫角色
鼠标悬浮到图片上切换到另一张图片
左键打开档案页面
档案页面右上角有一个小小的关闭按钮
档案左上角的图片可以切换
   左键单击切换封面时的另一张图
   左键双击切换大图立绘

# =开发者视角=
#### = =  基础数据更改= =
- 在img文件夹中使用 **文件名-1.webp 文件名-2 文件名-portrait.webp**来设置一个新角色的图片
 -1为初始图 -2为切换图 -portrait为立绘图 
>**e.g.**
 >FutabaRio-1.webp
 >FutabaRio-2.webp
 >FutabaRio-portrait.webp

- 在json文件夹中添加文件来增加新角色的档案信息
文件名为 文件名.json 需要与img文件中对应
>**e.g.**
 >FutabaRio.json

- 以下是json文件的格式  也可以直接去json文件夹中的文件查看/更改
在jsonMaker-original.html中可以更方便的的直接书写此项目的josn文件
```javascript
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
```
- json文件的修改可能不是一次就能成功的  因为信息长度等原因
    如果需要更改照片墙上的图片 只要在html文件中把row-item中的img的src属性改成新的图片文件名即可
    **名称需要和前面说的img json一致**
    原则上名字可以随便取 只要统一 但是为了防止不必要的bug和提高可辨识性 建议把图片名改成你对应那个角色的英语名/日语罗马音等诸如此类的纯英字节
### = =项目文件说明= =
- 文件中的index为主要文件（包含开发过程中的注释和调试痕迹）
- 如果你需要写入你的角色 为了方便你观察效果和制作 我准备了一个display-orginal.html文件
在里面有细致的指引 简单更改文字部分就可以让你直观看到窗口中档案的变化
- index-light.html把多余的部分删除 文件更小一点 如果不需要更改源码可以使用这一个
    
#### = =代码讲解= =
- 页面上的主要部分为6个*row*的*div*显示
- 滚动效果是css定义的``@keyframes``
- 对于每一行的滚动速度都设置了不同的变量在``:root``中 可以方便的更改流速
往下滚动后第二个衔接上的同样的*row-item*是在js里生成的
在执行之初 就会把本来*row*中的*row-item*复制一份到下方以完成衔接
        
- 没有学习过组件化开发 所以窗口就是直接写的单独的函数
- 窗口的背景为``filter:blur`` 实现毛玻璃效果
但是此属性对于部分浏览器可能不支持 
- 在窗口中大量元素以绝对定位的方式出现
- 标签中的[+][-]仅为装饰 无实义 只是作者来区分这个角色让自己喜欢/不太喜欢的点(当然是个人观点)
# = =计划= =
1. [制作中]加入文件自动生成json的文件和填入后自动生成的文件
(一个是空白的只需要你填就行 看不见效果也不用到编辑器中修改  一个是页面上 你去改元素值 看着差不多了直接生成)
几个input输入角色相关信息
最后输出直接是完整的json语句/文件
2. 加入点开窗口后背景不可互动的效果 预计用一个div实现
3. 加入名称切换
4. 加入动画
5. 背景图用json导入 不用直接在html中写路径 改用读取json
6. 打开角色播放对应的音乐+台词
    如果可能 设想一下加入动画切片 时间成本较高
    用卡片翻转效果 展示在卡片背面
7. 加入设置页面  调整部分可选择效果 用函数()在控制台执行打开设置页面
    在设置页面藏一个我自己的个人档案  加入信号干扰的效果在图片上

# = =相关语言= =
``HTML HTML5 CSS CSS3 JavaScript JSON``


# ================
# ===Translated 
# ===By Google:

# = =Project Background= =
This project is a wall of pictures that show my favorite anime characters. Each character can also open a window to view detailed information. This project is mainly completed using HTML, CSS, and JavaScript, and it is mainly for practicing front-end development skills and interest guidance. I shared this development result as a record of my own writing process. It is also a record of my own development process. Since I am a high school student, the update time may not be enough. I only made it in my local environment and ran it. If it needs to be deployed on a server environment, additional configuration and debugging may be needed.

# =User Perspective=
It should be a simple scrolling wall of pictures. The pictures are my favorite anime characters. When the mouse hovers over the picture, it switches to the next picture. Left-clicking on the archive page opens the profile page. The profile page has a small close button in the upper right corner. The image in the upper left corner can switch between the cover and the portrait. Left-clicking on the cover image switches to the next image, and left-clicking on the portrait image switches to the large portrait.

# =Developer Perspective=
#### = = Basic Data Change= =
- In the img folder, use **filename-1.webp filename-2 filename-portrait.webp** to set a new character's picture.
- -1 is the initial picture, -2 is the switch picture, and -portrait is the portrait picture.
- **e.g.**
 >FutabaRio-1.webp
 >FutabaRio-2.webp
 >FutabaRio-portrait.webp

- In the json folder, add a file to increase the information of a new character.
The file name is filename.json, which should correspond to the img file.
- **e.g.**
 >FutabaRio.json

- The following is the format of the json file. You can also check or modify the file in the json folder directly.
In the jsonMaker-original.html, it is easier to write the json file for this project.
```javascript
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
```
- The modification of the json file may not be successful all at once because of the length of the information.
If you need to change the pictures on the wall, you can simply change the src attribute of the img in the row-item in the html file to the new picture file name.
- **Name needs to be consistent with the img json name.**
- The principle is that the name can be anything you like, as long as it is consistent. However, to prevent unnecessary bugs and improve discriminability, it is recommended to change the picture name to the English name of the corresponding character, or the Japanese romanization of the name. 
### = =Project File Description= =
- The index file is the main file (with comments and debugging traces in the development process).
- If you need to write your own character, I prepared a display-orginal.html file for you to observe the effect and make the profile page.
In the file, there are detailed instructions and simple modifications to the text can make you see the changes in the profile window.
- index-light.html deletes unnecessary parts of the file and makes the file smaller. If you do not need to modify the source code, you can use this one.

#### = =Code Explanation= =
- The main part of the page is a set of 6 *row* *div* displays.
- The scrolling effect is defined by CSS ``@keyframes``.
- For each row's scrolling speed, different variables are set in ``:root``.
The second *row-item* that joins the same *row* is generated in js.
At the beginning, the *row* and *row-item* are copied to the next row to complete the connection.

- I have not learned component development yet, so the window is written as a separate function.
However, this attribute may not be supported by some browsers.
- In the window, a large number of elements are displayed in absolute position.
- The [+][-] in the tag are decorative and have no meaning. They are just used by the author to distinguish this character as one that I like or dislike (of course, it is a personal opinion).
# = =Plan= =
1. [In progress] Add file generation and automatic generation of json files and files to fill in.
(One is a blank one that you need to fill in, not visible and not need to modify in the editor. The other is a page on which you modify the element value, and it looks almost the same as the generated one directly.)
Several input boxes for character-related information.
The final output is a complete json statement or file.
2. Add the effect of the background window not being interactive when the window is opened.
The effect is implemented by a div.
3. Add name switching.
4. Add animation.
5. Use json to import background images, not directly write the path in the html file.
6. Open the character and play the corresponding music + dialogue.
If possible, imagine adding animation slices, which is time-consuming.
Use card flipping effect to show the card behind the picture.
7. Add a settings page to adjust some selectable effects. Use a function () in the console to open the settings page.
In the settings page, hide a personal profile and add signal interference effects on the picture.

# = =Related Languages= =
``HTML HTML5 CSS CSS3 JavaScript JSON``


# ================
# 作者的联系方式
### [How to contact me]
>QQ: 1215582857
邮箱[Email]: ystsfankui@hotmail.com
BiliBili: https://space.bilibili.com/1979641484
我只是个废物高二学生 所以我也留一下我的steam 欢迎找我玩
*I'm just a silly Chinese senior high school student in senior 2 (2024-2025) , so i also public my Steam, welcome to play with me*
Steam: https://steamcommunity.com/id/ApoxtleNeverDie
