# Bash 面向对象实现

## 目标
实现 Bash 的伪面向对象特性, 支持 class 的定义, 继承, 实例化

## 目标语法
```bash
@Class Animal

    mName="Animal";

    init()
    {
        mName="$1";
        echo "Init Animal Class";
    }

    getName()
    {
        echo -n "${mName}";
    }

    setName()
    {
        mName="$1";
    }

@End

@Class Dog : Animal

    init()
    {
        super "A";
    }

    @Override
    getName()
    {
        local res="$(super)";
        echo -n "A:$res";
    }
@End

@Class Home

    Dog mDog "XiaoHei";

    init()
    {
        (($# >= 1)) && mDog.setName "$1";
    }

    getDogName()
    {
        mDog.getName;
    }
@End

Home home "XiaoWang";

echo "HomeDog: $(home.getDogName)";
```
