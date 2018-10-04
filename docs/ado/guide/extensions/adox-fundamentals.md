---
title: Principes de base ADOX | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX, fundamentals
ms.assetid: 954476fc-5f72-4ada-ace5-d9acb27d18f8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5350fd4c4fd8fc447f3987ad502c49a2704e6762
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836437"
---
# <a name="adox-fundamentals"></a>Concepts de base d’ADOX
Microsoft® ActiveX® Data Objects Extensions pour le langage de définition de données et de sécurité (ADOX) est une extension pour les objets ADO et le modèle de programmation. ADOX inclut des objets pour la création de schémas et de modification, ainsi que de sécurité. S’agissant d’une approche basée sur l’objet de manipulation de schéma, vous pouvez écrire du code qui fonctionne par rapport aux données de différentes sources, quel que soit les différences dans les syntaxes natives.  
  
 ADOX est une bibliothèque complémentaire aux objets ADO principaux. Il expose des objets supplémentaires pour la création, modification et suppression d’objets de schéma, tels que tables et procédures. Il inclut également des objets de sécurité pour gérer les utilisateurs et groupes et pour accorder et révoquer des autorisations sur les objets.  
  
 Pour utiliser ADOX avec votre outil de développement, vous devez établir une référence à la bibliothèque de types ADOX. La description de la bibliothèque ADOX est « Microsoft ADO Ext. pour DDL et sécurité ». Le nom du fichier bibliothèque ADOX est Msadox.dll, et l’ID de programme (ProgID) est « ADOX ». Pour plus d’informations sur l’établissement de références aux bibliothèques, consultez la documentation de votre outil de développement.  
  
 Le fournisseur Microsoft OLE DB pour le moteur de base de données Microsoft Jet prend entièrement en charge ADOX. Certaines fonctionnalités d’ADOX ne sera pas gérées, en fonction de votre fournisseur de données.  
  
 Ce document suppose une connaissance pratique de Microsoft® Visual Basic®, langage de programmation et une connaissance générale d’ADO. Pour plus d’informations sur ADO, consultez le [Guide du programmeur ADO](../../../ado/guide/ado-programmer-s-guide.md). Pour plus d’informations vue d’ensemble sur ADOX, consultez les rubriques suivantes :  
  
-   [Modèle objet ADOX](../../../ado/reference/adox-api/adox-object-model.md)  
  
-   [Objets ADOX](../../../ado/reference/adox-api/adox-objects.md)  
  
-   [Collections ADOX](../../../ado/reference/adox-api/adox-collections.md)  
  
-   [Propriétés ADOX](../../../ado/reference/adox-api/adox-properties.md)  
  
-   [Méthodes ADOX](../../../ado/reference/adox-api/adox-methods.md)  
  
-   [Exemples de ADOX](../../../ado/reference/adox-api/adox-code-examples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des API ADOX](../../../ado/reference/adox-api/adox-api-reference.md)   
 [Exemples de Code ADOX](../../../ado/reference/adox-api/adox-code-examples.md)   
 [Collections ADOX](../../../ado/reference/adox-api/adox-collections.md)   
 [Constantes énumérées ADOX](../../../ado/reference/adox-api/adox-enumerated-constants.md)   
 [Méthodes ADOX](../../../ado/reference/adox-api/adox-methods.md)   
 [Modèle objet ADOX](../../../ado/reference/adox-api/adox-object-model.md)   
 [Objets ADOX](../../../ado/reference/adox-api/adox-objects.md)   
 [Propriétés ADOX](../../../ado/reference/adox-api/adox-properties.md)   
 [ADO multidimensionnel (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Guide du programmeur ADO](../../../ado/guide/ado-programmer-s-guide.md)
