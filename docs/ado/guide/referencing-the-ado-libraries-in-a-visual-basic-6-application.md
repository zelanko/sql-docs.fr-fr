---
title: Références aux bibliothèques ADO dans une Application Visual Basic 6 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8e37459c5e48fe817a3bdbb6a824550cf977f66
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696968"
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Références aux bibliothèques ADO dans une application Visual Basic 6
Pour importer les bibliothèques ADO dans une application Microsoft Visual Basic 6, vous devez définir une référence dans le projet Visual Basic.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Pour définir une référence aux bibliothèques ADO dans un projet Visual Basic  
  
1.  Créer un nouveau ou ouvrir un projet Visual Basic.  
  
2.  Cliquez sur le **projet** élément de menu, puis sélectionnez **références...**  à partir du Panneau de menu déroulant.  
  
3.  À partir de **références disponibles**, cochez la case **Microsoft ActiveX Data Objects *n.n* bibliothèque**, où ***n.n*** représente la dernière version numéro de version. Le **emplacement** champ ci-dessous doit identifier votre choix en tant que *$installDir\msado15.dll*, où *$installDir* représente le chemin d’accès du répertoire dans lequel la bibliothèque ADO a été installé.  
  
4.  Si vous avez l’intention d’utiliser ADO MD, répétez l’étape 3 pour sélectionner **Microsoft ActiveX Data Objects (multidimensionnel) *n.n* bibliothèque**. Le **emplacement** champ doit identifier ce choix en tant que *$installDir\msadomd.dll*.  
  
5.  Si vous avez l’intention d’utiliser ADOX, répétez l’étape 3 pour sélectionner **Microsoft ADO Ext. *n.n* pour DDL et la sécurité**. Le **emplacement** champ doit identifier ce choix en tant que *$installDir\msadox.dll*.  
  
6.  Cliquez sur **OK** pour finaliser la les références.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 L’installation de ADO copie également les bibliothèques de types suivantes des versions antérieures :  
  
-   *msado27.tlb*, bibliothèque de types 2.7 ADO  
  
-   *msado26.tlb*, bibliothèque de types 2.6 ADO  
  
-   *Msado25.tlb*, bibliothèque de types 2,5 ADO  
  
-   *Msado21.tlb*, bibliothèque de types 2.1 ADO  
  
-   *msado20.tlb*, bibliothèque de types 2.0 ADO  
  
 Si votre application doit utiliser une de ces bibliothèques ADO pour des raisons de compatibilité descendante, vous devez importer la version appropriée de la bibliothèque de types. Pour ce faire, suivez les procédures décrites dans la section précédente, en remplaçant *msado15.dll* par *msadoXX.tlb*, où *XX* représente le numéro de version que vous devez importer.
