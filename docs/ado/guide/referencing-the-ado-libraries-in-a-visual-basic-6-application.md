---
title: Référencement des bibliothèques ADO dans une application Visual Basic 6 | Microsoft Docs
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
ms.openlocfilehash: 25ea858995c884af202d3d80f4de675c9f4cda27
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923050"
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Références aux bibliothèques ADO dans une application Visual Basic 6
Pour importer les bibliothèques ADO dans une application Microsoft Visual Basic 6, vous devez définir une référence dans le projet Visual Basic.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Pour définir une référence aux bibliothèques ADO dans un projet Visual Basic  
  
1.  Créez un projet de Visual Basic existant ou ouvrez-en un.  
  
2.  Cliquez sur l’élément de menu **projet** , puis sélectionnez **références...** dans le panneau du menu déroulant.  
  
3.  Dans **Références disponibles**, activez la case à cocher de la **bibliothèque Microsoft ActiveX Data Objects *n. n* **, où ***n. n*** représente le numéro de version le plus récent. Le champ d' **emplacement** ci-dessous doit identifier votre choix en tant que *$INSTALLDIR \msado15.dll*, où *$INSTALLDIR* représente le chemin d’accès du répertoire dans lequel la bibliothèque ADO a été installée.  
  
4.  Si vous envisagez d’utiliser ADO MD, répétez l’étape 3 pour sélectionner la **bibliothèque Microsoft ActiveX Data Objects (multidimensionnelle) *n. n* **. Le champ d' **emplacement** doit identifier ce choix en tant que *$INSTALLDIR \msadomd.dll*.  
  
5.  Si vous envisagez d’utiliser ADOX, répétez l’étape 3 pour sélectionner **Microsoft ADO ext. *n. n* pour DDL et sécurité**. Le champ d' **emplacement** doit identifier ce choix en tant que *$INSTALLDIR \msadox.dll*.  
  
6.  Cliquez sur **OK** pour terminer la définition des références.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 L’installation d’ADO copie également les bibliothèques de types suivantes des versions antérieures :  
  
-   *msado27. tlb*, bibliothèque de types ADO 2,7  
  
-   *msado26. tlb*, bibliothèque de types ADO 2,6  
  
-   *Msado25. tlb*, bibliothèque de types ADO 2,5  
  
-   *Msado21. tlb*, bibliothèque de types ADO 2,1  
  
-   *msado20. tlb*, bibliothèque de types ADO 2,0  
  
 Si votre application doit utiliser l’une de ces bibliothèques ADO pour des raisons de compatibilité descendante, vous devez importer la version appropriée de la bibliothèque de types. Pour ce faire, suivez les procédures décrites dans la section précédente, remplacement de *msado15. dll* par *msadoXX. tlb*, où *XX* représente le numéro de version que vous devez importer.
