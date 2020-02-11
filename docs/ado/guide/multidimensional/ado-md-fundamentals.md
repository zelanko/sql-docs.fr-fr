---
title: Notions de base de ADO MD | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, fundamentals
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 690c7b58c336596485b9ade77f0c02928853cd2d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923201"
---
# <a name="ado-md-fundamentals"></a>Concepts de base d’ADO MD
Microsoft® ActiveX® Data Objects (multidimensionnel) (ADO MD) permet d’accéder facilement aux données multidimensionnelles à partir de langages tels que Microsoft Visual Basic®, Microsoft Visual C++®. ADO MD étend Microsoft ActiveX® Data Objects (ADO) pour inclure des objets spécifiques aux données multidimensionnelles, tels que les objets [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) et [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) . Avec ADO MD vous pouvez parcourir le schéma multidimensionnel, interroger un cube et récupérer les résultats.  
  
 Comme ADO, ADO MD utilise un fournisseur de OLE DB sous-jacent pour accéder aux données. Pour utiliser ADO MD, le fournisseur doit être un fournisseur de données multidimensionnelles (MDP) comme défini par le OLE DB pour la spécification OLAP. Un MDP présente des données dans des vues multidimensionnelles au lieu de vues tabulaires, ce qui explique comment un fournisseur de données tabulaires (TDP) présente des données. Pour plus d’informations sur la syntaxe et le comportement spécifiques pris en charge par votre fournisseur, reportez-vous à la documentation de votre fournisseur de OLE DB OLAP.  
  
 Ce document suppose une connaissance du langage de programmation Visual Basic et une connaissance générale de ADO et OLAP. Pour plus d’informations, consultez le [Guide du programmeur ADO](../../../ado/guide/ado-programmer-s-guide.md) et [OLE DB pour le traitement analytique en ligne (OLAP)](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Vue d’ensemble des données et des schémas multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [Utilisation de données multidimensionnelles](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [Utilisation d’ADO avec ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [Programmation avec ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Guide du programmeur ADO](../../../ado/guide/ado-programmer-s-guide.md)   
 [Extensions ADO pour la sécurité et le langage de définition de données (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Vue d’ensemble des schémas et des données multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmation avec ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Utilisation d’ADO avec ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Utilisation de données multidimensionnelles](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
