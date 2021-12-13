# styled-components 101

``` javascript
const Button = styled.button`
  font-size: 32px;
`;

const Button = styled.button`
  display: flex;
  &:hover {
    color: red;
  }
`;
```
별다른 것은 없고 js를 이용해서 css를 사용하는 것이므로 render 함수 이전에 코드가 호출되어야 한다.

그리고 콜론은 :: 가 원칙이다.

### CSS prop
```javascript
const Title = ({ id, children }) => {
  return (
    <h1
      id={id}
      css={`
        font-size: 2rem;
        font-weight: bold;
      `}
    >
      {children}
    </h1>
  )
};

```


</br>
</br>

## Installation and Setup

</br>
</br>

## Performance

</br>
</br>

## Exercises

</br>
</br>

## Dynamic Styles

</br>
</br>

## Exercises (pt. 2)

</br>
</br>
</br>
</br>

# Component Libraries
</br>
</br>

## Breadcrumbs

</br>
</br>

## Button
</br>
</br>

## Dynamic tags

</br>
</br>

## Escape Hatches

</br>
</br>
</br>
</br>

# Single Sourse of Styles

</br>
</br>
</br>
</br>

# In Summary

</br>
</br>
</br>
</br>

# Workshop: Mini Component Library

</br>
</br>

## ProgressBar

</br>
</br>

## Select

</br>
</br>

## IconInput
