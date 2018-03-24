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


