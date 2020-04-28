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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62fb1b89299af1f466e446c8adba422a841f0196
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923022"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Références aux bibliothèques ADO dans une application Visual C++
Pour utiliser la dernière version d’ADO dans une application Visual C++, utilisez la directive `#import` suivante :  
  
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
