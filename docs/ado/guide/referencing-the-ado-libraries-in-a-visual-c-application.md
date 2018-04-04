---
title: Référencer les bibliothèques ADO dans une Application Visual C++ | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology: drivers
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5cbc06a7ddf9452a96d2a3edff30b941a8d5f2b
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Référencer les bibliothèques ADO dans une Application Visual C++
Pour utiliser la dernière version de l’objet ADO dans une application Visual C++, utilisez ce qui suit `#import` directive :  
  
```  
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Pour utiliser ADO MD ou ADOX, vous devez importer *msadomd.dll* ou *msadox.dll*, en utilisant la syntaxe ci-dessus.  
  
## <a name="backward-compatibility"></a>Compatibilité descendante  
 Pour utiliser une version antérieure de l’objet ADO, remplacez *msado15.dll* ci-dessus avec l’une des bibliothèques de types suivantes.  
  
-   *msado27.tlb*, bibliothèque de types 2.7 ADO  
  
-   *msado26.tlb*, ADO 2.6 Type Library  
  
-   *Msado25.tlb*, bibliothèque de types 2,5 ADO  
  
-   *Msado21.tlb*, bibliothèque de types 2.1 ADO  
  
-   *msado20.tlb*, bibliothèque de types 2.0 ADO
