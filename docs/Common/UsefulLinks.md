# Полезные ссылки

1. [MDN](https://developer.mozilla.org/en-US/) - если вы хотите вспонить/узнать, что такое `this`, чем отличается `bind` от `call`, что такое `clusure` и `hoisting`, да и вообще, что-либо узнать о JS, то смело идите на MDN, это наиболее полная и подробная документация по JS на данный момент.
2. [Can I Use](https://caniuse.com/) - здесь вы можете узнать поддерживается какое-либо ключевое слово, API, CSS-свойство в том или ином браузере
3. Узнать как пользоваться Chrome Devtools правильно можно на [developer.chrome.com](https://developer.chrome.com/devtools), а так же в курсе от [CodeShcool](https://www.codeschool.com/courses/discover-devtools)
4. Event Loop. Для того, чтобы понять асинхронную природу JS можно ознакомиться с данными ресурвами:
    - [MDN: Event Loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop) - статья на MDN про Event Loop;
    - [Philip Roberts: What the heck is the event loop anyway? | JSConf EU 2014](https://www.youtube.com/watch?v=8aGhZQkoFbQ) - отличный доклад об Event Loop с хорошими примерами;
    - [Tasks, microtasks, queues and schedules](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/) - статья с хорошими примерами, подробно разъясняющая работу Event Loop с очередью задач;
5. Оптимизация производительности JS. **WARN**, не доверяйте никаким рекомендациям 10 раз их не перепроверив. Интерпретатор JS, JIT-компилятор, все в JS меняется, соотвественно, данный список может потерять актуальность, кроме того, тонкие оптимизации нужны крайне редко, если у вас есть проблема производительности, то скорее всего, это проблема в вашей бизнес логике, но тем не менее знать о возможных приемах оптимизации нужно:
    - [JS MythBusters](https://mythbusters.js.org/#/) - наиболее полный список возможных оптимизаций JS;
    - [Производительность JavaScript через подзорную трубу](https://www.youtube.com/watch?v=HPFARivHJRY&t=1535s) - отличный доклад Вячеслава Егорова о производительности JS;
    - [Performance tuning as the art of weather forecast](http://mrale.ph/blog/2013/04/29/performance-tuning-as-weather-forecast.html) - статья Вячеслава Егорова об оптимизациях производительности. Статья частично потеряала свою актуальность, но мысли, высказанные в ней, все еще актуальны;
    - [jsunderhood digest о производительности и оптимизациях](http://mrale.ph/blog/2015/04/12/jsunderhood.html) - все тот же Вячеслав Егоров отвечает на вопросы о производительности JS;
6. React.js. Сам по себе React - очень простая библиотека с точки зрения API и использования этого API, но если вы хотите понять, как React устроен, то эти ссылочки могут быть полезными:
    - [How to write your own Virtual DOM](https://medium.com/@deathmood/how-to-write-your-own-virtual-dom-ee74acc13060) - статья о том, как реализовать свой собственный Virtual DOM;
    - [Write your Virtual DOM 2: Props & Events](https://medium.com/@deathmood/write-your-virtual-dom-2-props-events-a957608f5c76) - продолжение первой статьи о реализации Virtual DOM;
    - [Build our own React.js!](https://swennemans.gitbooks.io/building-your-own-react-js/content/) - gitbook о реализации собственной react-like библиотеки;
    - [Getting Started with Redux](https://egghead.io/courses/getting-started-with-redux) - курс от Дэна Абрамова по Redux;
4. Функциональное программирование на js:
    - [Mostly adequate guide to FP](https://github.com/MostlyAdequate/mostly-adequate-guide) - отличная книга, с которой можно начать закомство с миром FP на JS;
    - [Fantasy Land Specification](https://github.com/fantasyland/fantasy-land) - спецификация функторов, апликативных функторов, монад и другого. Поможет углубить знания об абстракция, используемых в FP;
    - [Persistent Data Structures](https://medium.com/@dtinth/immutable-js-persistent-data-structures-and-structural-sharing-6d163fbd73d2) - статья о том, что такое Persistent Data Scructures и почему иимутабельные структуры данных могут быть не менее эффективными по расходу памяти, чем мутабельные;