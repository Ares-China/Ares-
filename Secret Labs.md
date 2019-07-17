秘密科技实验室
========
Secret Labs
--------------

现在秘密科技实验室可以自定义，这种建筑必须设置`SecretLab=yes`才行

    [Building]►SecretLab.PossibleBoons= (list of TechnoTypes)

随机的可以出现的东西

    [Building]►SecretLab.GenerateOnCapture= (boolean)

每次占领都重新随机一个东西，如果否的话在进入地图就定死，反复占领也都是一个单位，默认否

    [Boon]►SecretLab.RequiredHouses= (list of countries)

只有这个国家占领才能获得单位

    [Boon]►SecretLab.ForbiddenHouses= (list of countries)

除了这个国家其他国家占领都能获得单位
