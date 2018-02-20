�ο����ף�

[Redux �����ĵ�](http://cn.redux.js.org/)

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
        return [...state, action.value]
    } else {
        return state
    }
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
2. ���ǲ���ֱ�ӻ�����������һ����ͨ�� action ���� state �仯��
3. ע�⣬�����޸� state ��
4. ���� state ��һ�����飬Ȼ������Ҫ���������һ���µ�Ԫ�أ�����ز�Ҫֱ��ʹ�� push �������ӣ�Ӧ������������������һ���µ� state��
5. �������Ҫ�޸ģ��򷵻�Ĭ�ϵ� state ��
6. ���ͨ�� getState ����ȡ�� state��ֻ����������ѭ����ȡ����
7. state ��ѭ����
8. ��һ�� reducer ִ��ʱ��Ĭ��ֵ���� createStore ʱִ�У���
9. �ڶ��μ��Ժ� reducer ִ��ʱ��������һ��ֵ��
10 ÿ�� reducer ִ����ķ���ֵ��
11. getState ִ��ʱ�ķ���ֵ��

<br>
<b>��state ���޸�ԭ��</b>

1. ����Ҫ�ı� state ʱ������ԭ state ��
2. ��Ҫ�޸� state ʱ������һ���µ� state�����µ� state �Ͻ����޸Ĳ������µ� state��

<br>
��action��

1. ���� ``store.dispatch`` ����Ĳ������� action ��
2. �������ã����Ǹ��� store ����Ҫ��һ���£�������Ѿ��� reducer �ﶨ����ˣ���
3. Ȼ�� reducer �ᱻִ�У����ݴ����ֵ������Ԥ�ڵ��߼����£�
4. ��ִ�� createStore ʱ��reducer �ᱻִ��һ�Σ���ʱ action ��ֵ�� ``{type: "@@redux/INIT"}``��
5. action ������ type ���ԣ�

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

����˵�����ǿ���ͨ�����ģ��� store ���޸ĺ��Զ�ִ�����趨�Ļص���������������һ��ͬ����Ϊ��

����룺

```
import {createStore} from 'redux';

// ��˵�е� Reducer
function myReducer(state = [5, 4], action) {
    if (action.type === 'push') {
        return [...state, action.value]
    } else {
        return state
    }
}

// store����
let store = createStore(myReducer);
store.subscribe(function () {
    // ע�⣬thisָ�� undefined
    console.log('subscribe 1��', store.getState())
})
store.subscribe(function () {
    // ע�⣬thisָ�� undefined
    console.log('subscribe 2��', store.getState())
})
store.dispatch({type: 'push', value: 3})

console.log('after dispatch')
```

�����

```
subscribe 1�� (3) [5, 4, 3]
subscribe 2�� (3) [5, 4, 3]
after dispatch
```

Ҳ����˵��dispatch ִ����֮�����̾�ִ��֮ǰ subscribe �Ļص�������Ȼ����ִ�� dispatch ����Ĵ��롣

1. ���ж��ģ�subscribe���Ļص����������ᱻִ�У�
2. �ȶ��ĵ���ִ�У�
3. �ص�������� this��Ĭ���� undefined��
4. �ص����������ͨ�� store.getState() ����ȡֵ��

��ֹͣ������

1. ֹͣ�����ܼ򵥣�
2. ``let fn = store.subscribe(()=>{}) `` �᷵��һ��������ִ��һ�������������ֹͣ������

<h3>4��combineReducers �ϲ���� reducer</h3>

ΪʲôҪ�ϲ���� reducer ��

ԭ���ǣ�

1. һ������£�����ֻ��һ�� store ��
2. ���ǿ���ʱ�Ķ��������ȵģ�����һ��ģ�����һ�� reducer ��
3. ���Ա�Ȼ����Ӧ������ж�� reducer ���������ʣ���Щ reducer ֮��Ӧ���ǽ���ģ�
4. ������ store ֻ��һ���� createStore ʱ��Ҳֻ��һ���������������Ǳ���Ѷ�� reducer �ϲ����ٴ��� createStore ��
5. �����Ϊʲô����Ҫ�ϲ���� reducer ��
6. ������ô�ϲ���ʹ�� ``combineReducers(object)`` ���ɣ�

����ʾ����

```
function First(state = {text: 'First', index: 0}, action) {
    state.index++;
    return state;
}

function Second(state = {text: 'Second', index: 0}, action) {
    // �����ڳ�ʼ����combineReducers��ʱ���ᱻִ�� 2 �Σ�У�� reducer������Ҫ����ע��һ�¡�
    // ��һ���� {type: "@@redux/INIT"}�����ֵ�����洢������
    // ��һ����Ϊ�˼���ʼ��ʱ������ֵ�ǲ��� undefined����������״�
    // �ڶ����� {type: "@@redux/PROBE_UNKNOWN_ACTION_����ַ�����"}
    // �ڶ�����Ϊ�˲��Ե� type Ϊ�����ʱ���ǲ��ǻ᷵��undefined������������û��ÿ�ζ����� state ��ֵ��
    // ������� undefined����ᱨ��������һ�� reducer ��⣩
    // ���⣬�����ε�ֵ������洢��������Ϊ�Ǵ����ԣ����������� reducer ��д��ĳЩ�и����õĴ���
    // �����޸�ĳ�� reducer ����������֮��ı�������ô�ͳ����ˣ���Ϊ��Ԥ��ֻӦ���޸�һ�Σ���ʵ���޸������Σ�
    // ����Ӧ�þ��������и����õĴ���д�� reducer ����
    console.log('second action: ', action)
    // ����ֻ�ǲ��Դ��룬ʵ����
    state.index++;
    return state;
}

// �ϲ�����reducer������һ���µ� reducer
// �ϲ��󣬷����µ� state ���µ���һ�����󣬽ṹ�� { First: {}, Second: {} }
// First �� state �����ڷ��ض���� First �����
// Second ͬ��
// ��ִ�����������ʱ�򣬻����һ�δ���� reducer
let fn = combineReducers({
    First,
    Second
})
console.log('after combineReducers')

let store = createStore(fn)

// ��ʼ��ȡĬ�ϵ� state��ע�⣬��ʱ���� reducer �Ѿ���ִ�й�һ���ˣ���ʼ���������� index Ϊ 1
console.log(store.getState())   // {"First":{"text":"First","index":1},"Second":{"text":"Second","index":1}}

// ����һ�� action����ʱ��ÿ�� reducer ���ᱻִ��
store.dispatch({type: ''});

// ��ȡ��ʱ��ֵ������������index�����ı���
console.log(store.getState())   // {"First":{"text":"First","index":2},"Second":{"text":"Second","index":2}}
```

���ģ�

1. combineReducers ʱ������鴫��� reducer �����Σ���ʼ�������� type����
2. ִ����󣬻᷵��һ���µ� reducer ��ע�⣬����µ� reducer ���Լ��������� reducer �ٴ� combineReducers ����
3. ��� reducer �����֮�󣬱� createStore ����ʱ getState ���ص� state ��һ���������ṹ����
4. ��� state ���Ǹ��� reducer �� kv ��ʽ��϶��ɵġ�������˵�� key �� combineReducers ʱ��ÿ�� reducer �� key ���� value ��ÿ�� reducer �� state��
5. �絥�� First �� state �� ``{"text": "First", "index": 1}``����ô��Ϻ��µ� state ��Ϊ��``{"First": {"text": "First", "index": 1}}``��
6. ÿ��ִ�� action ʱ��������ִ��ÿһ�� reducer�������㴫���˷��� First �� type ���� js ʵ��ִ���У���������֪���㴫��� type �Ƿ�����һ�� reducer ��������ÿ�� reducer ����ִ�У�
7. ������˵��Ĭ������£��������κ�һ�� type ����Ӧ�÷���Ĭ�ϵ� state ����ȽϺ����������������󣩣�

<br>
�����̫���ף��뽫���ϴ������к󣬲鿴����̨���������������⣻

<h3>5���з� action </h3>

�ڡ�4���Ļ����ϣ����ǽ���� reducer ��ϵ���һ��

�����һ�����⣬�Ǿ��ǵ�������Ҫ�޸�һ�� state ʱ����Ƚ��鷳�����磺``store.dispatch({type: 'add', value: '123'})``

�������ǲ����ԣ������������ڣ���϶�̫�ߣ�������Ҫ֪�� reducer �ڲ�������������� type �ֶε�ֵ��ʲô����������ֶβ��ܱ����ģ���

�ڼ򵥵�С��Ӧ���У��⵹�������⣬������Դ���Ӧ�õ�ʱ���Ⲣ����һ���õķ�����

����취��

1. �� actions ������װ��һ�� js �ļ��У�
2. �� actions �� type ��Ϊ������
3. �� reducer �type ��ֵȡ���������
4. ������Ҫʹ��ĳ�� action ʱ���������������Ϊ type ���ɣ�
5. �������ǲ���Ҫ���� type ������ʲôֵ��ֻ��Ҫȷ��ͬһ�� reducer �£����� type ���ظ����ɣ�
6. Ϊ�˽��ÿ�ζ�Ҫд type �����⣬���ǽ����� action �����Ϊ����װ��һ��������
7. �������Ŀ��������һ�� action �������������Ҫ�ı�����
8. ��������һ��������Ȼ��������һ������������Ҫ�� action ���ٽ���� action ��Ϊ dispatch �Ĳ�������ȥ���� ok �ˣ�

��һ����򵥵�ʾ����

```
// actions.js
/*
 * action �� type �ĳ���
 */
export const ADD_ITEM = 'ADD_LIST';
export const REMOVE_LAST_ITEM = 'REMOVE_LAST_ITEM'

/*
 * action ��������
 */
// ��ӽ� state
export function addToList(item) {
    return {type: ADD_ITEM, item}
}

// �Ƴ����һ����ӵ�����
export function removeFromList() {
    return {type: REMOVE_LAST_ITEM}
}
```


```
// app.js
import {createStore} from 'redux'
import {ADD_ITEM, addToList, REMOVE_LAST_ITEM, removeFromList} from './actions'

function List(state = [], action) {
    // ע�⣬û���޸�ԭ state
    if (action.type === ADD_ITEM) {
        return [...state, action.item]
    } else if (action.type === REMOVE_LAST_ITEM) {
        let arr = [...state]
        arr.pop()
        return arr
    } else {
        return state;
    }
}

let store = createStore(List)
store.subscribe(() => {
    console.log(store.getState())
})
store.dispatch(addToList('first'))
store.dispatch(addToList('second'))
store.dispatch(removeFromList())
```

��������

```
["first"]
["first", "second"]
["first"]
```

������

1. action.js �������ɳ�������������
2. action.js ���װ�˴��� action �ĺ�����
3. app.js �д�� reducer ��reducer ���ж� action.type ʱ��ֱ���жϵ�������ĳ������������Լ�д���ַ�����
4. app.js �reducer �� state δ�޸�ʱ������Ĭ�� state�����޸ģ��򷵻�ȫ�µ� state ��
4. app.js �ͨ�� addToList �� removeFromList ���� action ������ֻ������Ҫ��ʲô���������ʲô����������ʵ�� action �ṹ��ʲô��
5. app.js �reducer ��ȫ���Է�װ������һ�� js �ļ������һ��ר�ŵ� reducer.js ������ reducer�������ڸ���Ӧ���У����Ӽ�����һЩ��

<h3>6��Redux �� React ���ʹ��</h3>

>��װ

���˰�װ redux �⣬��Ҫ��װ react-redux

```
npm install --save react-redux
```

<h3>7��</h3>
<h3>8��</h3>
<h3>9��</h3>
<h3>10��</h3>