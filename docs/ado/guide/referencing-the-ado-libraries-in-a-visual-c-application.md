---
title: "Référencer les bibliothèques ADO dans une Application Visual C++ | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: "“drivers”"
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3bbb3a9345c969d5d5bc038f31f7f7bc0b731c40
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Référencer les bibliothèques ADO dans une Application Visual C++
Pour utiliser la dernière version de l’objet ADO dans une application Visual C++, utilisez ce qui suit `#import` directive :  
  
```  
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Pour utiliser ADO MD ou ADOX, vous devez importer *msadomd.dll* ou *msadox.dll*, en utilisant la syntaxe ci-dessus.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Pour utiliser une version antérieure de l’objet ADO, remplacez *msado15.dll* ci-dessus avec l’une des bibliothèques de types suivantes.  
  
-   *msado27.tlb*, bibliothèque de types 2.7 ADO  
  
-   *msado26.tlb*, bibliothèque de types 2.6 ADO  
  
-   *Msado25.tlb*, bibliothèque de types 2,5 ADO  
  
-   *Msado21.tlb*, bibliothèque de types 2.1 ADO  
  
-   *msado20.tlb*, bibliothèque de types 2.0 ADO
