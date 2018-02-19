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
function myReducer(state = [5, 4], action) {
    if (action.type === 'push') {
        state.push(action.value)
    }
    return state
}

// store����
let store = createStore(myReducer);

// ��������������ķ���ֵ������������Ҫ�ķ���ֵ
store.dispatch({type: 'push', value: '123'})

console.log('after dispatch��', store.getState())
console.log('end')
```

�����

```
after dispatch�� (2) [5, 4]
end
```

������

��Reducer��

1. ��ν�� Reducer ����һ��������������� myReducer����
2. ����һ���� state ���������⣨�ַ���������ȣ���������Ҫ��������ݣ����Ǵ�������ģ�
3. ��һ�� state ��ֵ��ȡ��Ĭ��ֵ��֮�� state ��ֵ��ȡ�� <b>֮ǰ reducer �ķ���ֵ����Ҫ����</b>��
4. ��������һ�����󣬵����� dispatch ʱ�����������Ϊ������������뱾������
5. ����˵����ν�� reducer������ָ����һ��������ÿ����Ҫ�޸�/��ȡ������ʱ�򣬾ͻ�ִ�����������Ȼ��������߼������޸�/��ȡ����Ҫ���Ǹ� state����󷵻���� state ��
6. ��һ��ִ�� reducer ������ createStore ��һ��ʱִ�еġ�

<br>

��state��

1. ����˵������ֵ���Ǵ��������ģ����� myReducer ������Ĳ��� state����
2. ���ǲ���ֱ�ӻ�����������һ����ͨ�� action ���޸� state��
3. ���ͨ�� getState ����ȡ���� state��ֻ����������ѭ����ȡ����
4. state ��ѭ����
5. ��һ�� reducer ִ��ʱ��Ĭ��ֵ���� createStore ʱִ�У���
6. �ڶ��μ��Ժ� reducer ִ��ʱ��������һ��ֵ��
7. ÿ�� reducer ִ����ķ���ֵ��
8. getState ִ��ʱ�ķ���ֵ��

<br>

��action��

1. ���� ``store.dispatch`` ����Ĳ������� action ��
2. �������ã����Ǹ��� store ����Ҫ��һ���£�������Ѿ��� reducer �ﶨ����ˣ���
3. Ȼ�� reducer �ᱻִ�У����ݴ����ֵ������Ԥ�ڵ��߼����£�
4. ��ִ�� createStore ʱ��reducer �ᱻִ��һ�Σ���ʱ action ��ֵ�� ``{type: "@@redux/INIT"}``��

<br>

��getState��

1. dispatch ���� action �󣬲�����ֱ�ӻ�� state ��ֵ���䷵��ֵ�� dispatch �Ĳ������� action ����
2. ���������Ҫ�� action ��Ϻ�ͨ�� getState ����ȡ����ȡ����ֵ��
3. getState ȡֵ��ÿ�� reducer ִ�����ķ���ֵ��
4. ִ�� getState ʱ������ִ�� reducer ������ȡ֮ǰִ�� reducer ʱ�ķ���ֵ��������� state ���洢�����ˣ���

<br>

��store��

1. ���ϼ�����������һ�� store Ϊ��λ��ʹ�õģ�������ı��� store ����
2. �����ж�� store������ storeA �� storeB ����Ȼ����֮���ǲ��ụ����ŵģ��� storeA ���� dispatch ��ֻ��ִ�� storeA �� reducer ��������ִ�� storeB �ģ�

<br>

��ͬ����

1. dispatch ��ͬ����Ϊ��
2. getState Ҳ��ͬ����Ϊ��
3. ���Ե��� dispatch �󣬿�������ͨ�� getState ��ȡ���µ� state ��ֵ��


<br>
�ܽ᣺

1. Redux ��ʵ�ʣ����Ǵ���һ�� store ;
2. Ȼ������� store ��Ϊ���ģ�ͨ�� action ������dispatch������ reducer ���ص���������Ȼ���޸� state �����ͨ�� getState ����ȡ��ǰ�� state��
3. �������ǻ��������������죻

<h3>3�����ĸ��� subscribe</h3>

����˵�����ǿ���ͨ�����ģ��� store ���޸ĺ��Զ�ִ�����趨�Ļص�������



<h3>4��</h3>
<h3>5��</h3>
<h3>6��</h3>
<h3>7��</h3>
<h3>8��</h3>
<h3>9��</h3>
<h3>10��</h3>