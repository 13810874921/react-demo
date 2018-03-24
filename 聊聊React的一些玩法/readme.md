<h3>1����д��</h3>

������д React ���ʱ���ο��ٷ��ĵ�д����һҪ���� state����Ҫ�󶨺����� this������д�����£�

```
class DEMO extends React.Component {
    constructor() {
        super();
        this.state = {
            count: 0
        };
        this.kick = this.kick.bind(this);
    }

    render() {
        return <div>
            <button onClick={this.kick}>�������</button>
            ���Ѿ������{this.state.count}�Ρ�
        </div>;
    }

    kick() {
        this.setState({
            count: this.state.count + 1
        });
    }
}
```

Ȼ��������д�����鷳���ҳ��鷳���������н��������д�����£�

```
class DEMO extends React.Component {
    state = {
        count: 0
    };

    render() {
        return <div>
            <button onClick={this.kick}>�������</button>
            ���Ѿ������{this.state.count}�Ρ�
        </div>;
    }

    kick = () => {
        this.setState({
            count: this.state.count + 1
        });
    };
}
```

<b>Ч����</b>

1. ��ȥд���캯�����鷳������ֱ�������� class �¸���ֱ�ۣ�
2. ��ȥд bind �Ķ����������������Ϊ����д bind ������ bug �Ŀ��ܣ�

���ĸĶ������㣺

1. state ���� constructor ������������ֱ���� class ��д������д����һ�������ԣ�������Ҫ���ģ�babel ���Խ���ʶ��ת��Ϊ es5 ���룻
2. ����ͨ����ͷ��������������Ϊ��ͷ������ this������������ʱ����������������ٶ���ͨ�� ``bind()`` ���� this��

<b>ʵ�ַ�ʽ��</b>

1. ����ʵ�ַ�ʽ��ͨ�� babel ��ʵ�ֵģ�
2. ����ʵ�ַ�ʽ���Բο�����ƪ���� ``babel-loader`` ��˵����[������� 5.2��֧��������](https://github.com/qq20004604/webpack-study/tree/master/5%E3%80%81Loader/babel_loader#52%E6%94%AF%E6%8C%81%E6%96%B0%E7%89%B9%E6%80%A7)��
3. ���Ϸ���������Ϥwebpack�������� webpack ���̵�����£�ֻҪ��˵��ȥ���Ϳ��ԣ��ǳ��򵥣���װһ�� npm �����������ļ����һ�����ü��ɣ���
4. ������ԵĻ�����˳�ָ��ҵ� github һ�� star��лл��
5. [ʾ��DEMO��Ŀ](https://github.com/qq20004604/react-demo/tree/master/%E8%81%8A%E8%81%8AReact%E7%9A%84%E4%B8%80%E4%BA%9B%E7%8E%A9%E6%B3%95)��

<h3>2���� React ��Դͨ��CDN����</h3>

��Ȼ React ����󣬲����󣬵��Ƕ������ǣ���û��Ҫֱ�Ӵ�������ǵ� js �����еģ�ʹ�� CDN �Ǹ��õ�ѡ��

������˵���������ϵĴ��룬��������ʹ��һ��Ĵ����ʽ���� ``react`` �� ``react-dom`` ��������ǵ� js �ļ��У��������ļ���С��Լ�ǣ�

```
app.js        // 33 KB
vendor.js        // 106 KB
```

���� React ͨ�� CDN ��������Ǵ����� js ��С��Ϊ��

```
app.js        // 33 KB
vendor.js        // 8 KB
```

��֮���Լ 100 KB �Ĵ�С��࣬���� ``react`` �� ``react-dom`` �� 2 ������Լ�����Ĵ�С��

<b>����������</b>

������ ``webpack.config.js`` ���� webpack �������ļ������������ webpack �������ԣ����һ���������ԣ�

```
externals: {
    "react": "React",
    "react-dom": "ReactDOM"
}
```

��Σ��� html ģ���ļ������ CDN ���������в��� head ��ǩ�С�

��ʾ���У��� index.html �ļ���������� webpack ͨ�� ``html-webpack-plugin`` ������õġ�

```
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
```

Ȼ��͸㶨�ˡ�

����ԭ����ο�����һƪ���� [9���ⲿ��չ��Externals��](https://github.com/qq20004604/webpack-study/tree/master/9%E3%80%81%E5%A4%96%E9%83%A8%E6%89%A9%E5%B1%95%EF%BC%88Externals%EF%BC%89)��

