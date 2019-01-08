---
title: Espaces de noms | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db90ecbc083a887a9845542b73e50bae6bf61e1e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52534745"
---
# <a name="namespaces"></a>Espaces de noms
Le format de persistance XML dans ADO utilise quatre espaces de noms suivants.  
  
## <a name="remarks"></a>Notes  
 Le format de persistance XML dans ADO utilise quatre espaces de noms suivants.  
  
|Prefix|Description|  
|------------|-----------------|  
|s|Fait référence à l’espace de noms « XML-Data » contenant les éléments et attributs qui définissent le schéma de l’ensemble d’enregistrements actuel.|  
|DT|Fait référence à la spécification de définitions de type de données.|  
|rs|Fait référence à l’espace de noms des éléments conteneur et des attributs spécifiques aux propriétés de jeu d’enregistrements ADO et des attributs.|  
|z|Fait référence au schéma de l’ensemble de lignes en cours.|  
  
 Un client ne devez pas ajouter ses propres balises à ces espaces de noms, tel que défini par la spécification. Par exemple, un client ne doit pas définir un espace de noms « urn : schemas-microsoft-rowset », puis écrire quelque chose comme « rs : MaPropreBalise ». Pour en savoir plus sur les espaces de noms, consultez le [espaces de noms W3C dans la recommandation XML](https://www.w3.org/TR/REC-xml-names/).  
  
> [!IMPORTANT]
>  L’ID de la balise de schéma doit être « RowsetSchema » et l’espace de noms utilisé pour faire référence au schéma de l’ensemble de lignes en cours doit pointer vers « #RowsetSchema ».  
  
 Notez que le préfixe de l’espace de noms - la partie entre le signe deux-points et le signe égal - est arbitraire.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 L’utilisateur peut définir cette option pour être n’importe quel nom, que ce nom est utilisé partout dans le document XML. ADO écrit toujours « s », « rs », « dt » et « z », mais ces préfixes ne sont pas codées en dur dans le composant de chargement.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
