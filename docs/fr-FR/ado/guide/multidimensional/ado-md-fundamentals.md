---
title: Notions de base ADO MD | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, fundamentals
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92a245f79f7425d44aeb911edff479d80c08b08f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ado-md-fundamentals"></a>Notions de base ADO MD
Microsoft® ActiveX® Data Objects (multidimensionnel) (ADO MD) fournit un accès facile aux données multidimensionnelles à partir de langages tels que Microsoft Visual Basic®, Microsoft Visual C++®. ADO MD étend Microsoft ActiveX® Data Objects (ADO) pour inclure des objets spécifiques aux données multidimensionnelles, telles que la [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) et [ensemble de cellules](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objets. Avec ADO MD, vous pouvez parcourir un schéma multidimensionnel, un cube de requête et récupérer les résultats.  
  
 Comme ADO, ADO MD utilise un fournisseur OLE DB sous-jacent pour accéder aux données. Pour utiliser ADO MD, le fournisseur doit être un fournisseur de données multidimensionnelles (MDP) tel que défini par la spécification OLE DB pour OLAP. Un MDP présente les données dans des vues multidimensionnelles au lieu des affichages tabulaires, qui est la façon dont un fournisseur de données tabulaires (TDP) présente les données. Consultez la documentation de votre fournisseur OLE DB pour OLAP pour plus d’informations sur la syntaxe spécifique et le comportement pris en charge par votre fournisseur.  
  
 Ce document suppose une connaissance pratique du langage de programmation Visual Basic et une connaissance générale d’ADO et OLAP. Pour plus d’informations, consultez la [Guide du programmeur ADO](../../../ado/guide/ado-programmer-s-guide.md) et [OLE DB pour OLAP Online Analytical Processing ()](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Vue d’ensemble des données et des schémas multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [Utilisation de données multidimensionnelles](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [Utilisation d’ADO avec ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [Programmation avec ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Guide du programmeur ADO](../../../ado/guide/ado-programmer-s-guide.md)   
 [ADO Extensions de langage de définition de données et de sécurité (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Vue d’ensemble des schémas et données multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmation avec ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [À l’aide d’ADO avec ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Utilisation de données multidimensionnelles](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
