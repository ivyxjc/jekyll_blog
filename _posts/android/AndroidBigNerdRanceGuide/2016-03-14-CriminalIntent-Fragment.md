---
layout: post
title: Criminal程序中Fragment相关内容
category: Android
tags: [android,androidfragment,fragment,listfragment,adapter,listview,arrayadapter]
keywords:
description:
---


## Fragment与Activity数据传送

Fragment传送数据到Activity

```java
Intent i=new Intent(getActivity(),CrimeActivity.class);
i.putExtra(CrimeFragment.EXTRA_CRIME_ID,c.getId());
startActivity(i);
```

Activity中接受数据

```java
@Override
public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    UUID crimeId=(UUID)getActivity().getIntent()
            .getSerializableExtra(EXTRA_CRIME_ID);

    mCrime=CrimeLab.get(getActivity()).getCrime(crimeId);
}
```
