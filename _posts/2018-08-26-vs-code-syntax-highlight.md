---
title: Как изменить цвета подсветки синтаксиса в VS Code
layout: post
tags: [vs_code, css, веб_дизайн]
thumbnail: /Images/BrK-p8PMBERKd8NTmD04oA.png
---
Решить, вроде бы, банальный для редактора кода вопрос из заголовка, в VS Code оказалось непросто. В Sublime Text для этого достаточно распаковать файл темы, найти нужное значение и поменять цвет. Но мне нужен был официально бесплатный для коммерческого использования редактор и из тех, что я пробовал, VS Code показался самым нормальным (еще потыкал Brackets и Atom). Но, как это обычно бывает, чем дольше чем-то пользуешься, тем больше косяков находишь. Особенно у Майкрософт, да. Тут они решили не искать простых путей (по крайней мере, для пользователя). Хотите поменять один цвет? Вам придется либо создавать тему с нуля, либо собирать по крупицам рецепт ниже. Может этот пост сэкономит кому-то время и нервы.

Будем менять цвета подсветки на примере темы Solarized Dark и CSS.

1. Открываем настройки.
2. В пользовательские настройки добавляем следующую конструкцию:

`````
“editor.tokenColorCustomizations”: {
    “[Solarized Dark]”: {
        “textMateRules”: [
            {
                “scope”: “entity.other.attribute-name.class.css”,
                “settings”: {
                “foreground”: “#e9a449”
                }
            },
        ],
    },
},
````
## Как изменить другую тему, другие параметры и другие языки

Название темы в квадратных скобках просто заменяете на вашу. Вам нужно узнать значение scope для того элемента, который вы хотите изменить. Для этого откройте файл с кодом. Вызовите командную строку (Ctrl+Shift+P). Наберите "Developer: Inspect Editor Tokens and Scopes" и нажмите Enter. При клике на элемент, появится всплывающее окно:

![скриншот-1]({{site.baseurl}}/Images/BrK-p8PMBERKd8NTmD04oA.png)

Оно сразу предлагает строку с называнием параметра (тот самый scope) и текущим цветом — entity.other.attribute-name { “foreground”: “#93A1A1” }. Но, это не то, что нам нужно! По-крайней мере в данном случае, этот параметр изменит цвет всех селекторов (и классов, и id). Но я хочу задать для каждого свой цвет. Поэтому нам нужен первый параметр из списка ниже. То есть entity.other.attribute-name.class.css. У идентификатора будет похожая картина, только scope будет entity.other.attribute-name.id.css.

А вот после применения настроек scope также поменяется на нужный:

![скриншот-2]({{site.baseurl}}/Images/Gl2CS_N3358j5fO73nX9A.png)

Я оставил в коде запятые на случай, если вы захотите добавить других цветов и другие параметры на уровни выше.