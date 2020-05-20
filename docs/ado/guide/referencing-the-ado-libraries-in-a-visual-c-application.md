---
title: Référencement des bibliothèques ADO dans une application Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: rothja
ms.author: jroth
ms.openlocfilehash: a790ace40aa31324ce8b22127d8f6948ae86e059
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764760"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Références aux bibliothèques ADO dans une application Visual C++
Pour utiliser la dernière version d’ADO dans une application Visual C++, utilisez la `#import` directive suivante :  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Pour utiliser ADO MD ou ADOX, vous devez importer *msadomd. dll* ou *msadox. dll*à l’aide de la syntaxe ci-dessus.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Pour utiliser une version antérieure d’ADO, remplacez *msado15. dll* ci-dessus par l’une des bibliothèques de types suivantes.  
  
-   *msado27. tlb*, bibliothèque de types ADO 2,7  
  
-   *msado26. tlb*, bibliothèque de types ADO 2,6  
  
-   *Msado25. tlb*, bibliothèque de types ADO 2,5  
  
-   *Msado21. tlb*, bibliothèque de types ADO 2,1  
  
-   *msado20. tlb*, bibliothèque de types ADO 2,0
