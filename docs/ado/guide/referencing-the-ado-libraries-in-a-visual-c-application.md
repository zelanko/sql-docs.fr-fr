---
title: Références aux bibliothèques ADO dans une Application Visual C++ | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 772dbc55fdeb3b038399a3740be472497666e4da
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51290785"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Références aux bibliothèques ADO dans une application Visual C++
Pour utiliser la dernière version de ADO dans une application Visual C++, utilisez la commande suivante `#import` directive :  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Pour utiliser ADO MD ou ADOX, vous devez importer *msadomd.dll* ou *msadox.dll*, en utilisant la syntaxe ci-dessus.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Pour utiliser les versions précédentes d’ADO, remplacez *msado15.dll* ci-dessus avec l’une des bibliothèques de types suivantes.  
  
-   *msado27.tlb*, bibliothèque de types 2.7 ADO  
  
-   *msado26.tlb*, bibliothèque de types 2.6 ADO  
  
-   *Msado25.tlb*, bibliothèque de types 2,5 ADO  
  
-   *Msado21.tlb*, bibliothèque de types 2.1 ADO  
  
-   *msado20.tlb*, bibliothèque de types 2.0 ADO
