<h3>1����װ</h3>

```
npm install --save redux react-redux redux-devtools
```

<h3>2������ʾ��</h3>

���� DEMO��

```
// ����
import {createStore} from 'redux';

// ��˵�е� Reducer
function myReducer(state = [5, 4, 3], action) {
    let number = [5, 4, 3];
    let test = {
        a: 0,
        b: 1,
        c: 2
    }
    if (number[test[action.type]]) {
        return number[test[action.type]]
    } else {
        return 'not Found'
    }
}

// store����
let store = createStore(myReducer);

// ��������������ķ���ֵ������������Ҫ�ķ���ֵ
store.dispatch({type: 'a'})

// ���ǵķ���ֵ����Ҫͨ�� store.getState ����ȡ
console.log(store.getState())
```

������

��Reducer��

1. ��ν�� Reducer ����һ��������������� myReducer����
2. ����һ���� state ���������⣨�ַ���������ȣ�����������ҪӰ����Ǹ�������
3. ��������һ�����󣬵����� dispatch ʱ�����������Ϊ������������뱾������
4. ����˵����ν��reducer������ָ����һ��������ÿ����Ҫ�޸ı�����ʱ�򣬾ͻ�ִ�����������Ȼ��������߼������޸�/��ȡ����Ҫ���Ǹ� state��

<br>

��state��

1. ����˵������ֵ���Ǵ��������ģ����� myReducer ������Ĳ��� state����
2. ���ǲ���ֱ�ӻ�����������һ����ͨ�� action ����ȡ/�޸� state��
3. ����ȡ���ǿ� dispatch ��ȡ������ͨ�� getState ����ȡ��

<br>

��action��

1. ���� ``store.dispatch`` ����Ĳ������� action ��
2. �������ã����Ǹ��� store ����Ҫ��һ���£�������Ѿ��� reducer �ﶨ����ˣ���
3. Ȼ�� reducer �ᱻִ�У����ݴ����ֵ������Ԥ�ڵ��߼����£�
4. �����Ҫ��ȡֵ����ô�� return �������ֵ��

<br>

��getState��

1. dispatch ���� action �󣬲�����ֱ�ӻ�� state ��ֵ���䷵��ֵ�� dispatch �Ĳ������� action ����
2. ���������Ҫ�� action ��Ϻ�ͨ�� getState ����ȡ����ȡ����ֵ��

<br>

��store��

1. ���ϼ�����������һ�� store Ϊ��λ��ʹ�õģ�������ı��� store ����
2. �����ж�� store������ storeA �� storeB ����Ȼ����֮���ǲ��ụ����ŵģ��� storeA ���� dispatch ��ֻ��ִ�� storeA �� reducer ��������ִ�� storeB �ģ�

<br>
�ܽ᣺

1. Redux ��ʵ�ʣ����Ǵ���һ�� store ;
2. Ȼ������� store ��Ϊ���ģ�ͨ�� action ������dispatch������ reducer ���ص���������Ȼ���޸�/��ȡ state �����ͨ�� getState ����ȡ��ǰ�� state��
3. �������ǻ��������������죻

<h3>3��</h3>


<h3>4��</h3>
<h3>5��</h3>
<h3>6��</h3>
<h3>7��</h3>
<h3>8��</h3>
<h3>9��</h3>
<h3>10��</h3>