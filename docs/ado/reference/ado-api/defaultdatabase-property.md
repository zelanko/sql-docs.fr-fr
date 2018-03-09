---
title: "Propriété DefaultDatabase | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c4220d8551d7aa9d1bd37f0770474214bc14209
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="defaultdatabase-property"></a>Propriété DefaultDatabase
Indique la base de données par défaut pour un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur, qui correspond au nom d’une base de données disponible à partir du fournisseur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **DefaultDatabase** propriété pour définir ou retourner le nom de la base de données par défaut d’un spécifique **connexion** objet.  
  
 S’il existe une base de données par défaut, les chaînes SQL peuvent utiliser une syntaxe non qualifiée pour accéder aux objets dans cette base de données. Pour accéder aux objets dans une base de données autre que celui spécifié dans le **DefaultDatabase** propriété, vous devez qualifier les noms d’objet avec le nom de la base de données souhaitée. Lors de la connexion, le fournisseur écrit les informations de base de données par défaut pour le **DefaultDatabase** propriété. Certains fournisseurs n'autorisent qu’une seule base de données par connexion, auquel cas vous ne pouvez pas modifier le **DefaultDatabase** propriété.  
  
 Certaines sources de données et les fournisseurs ne peuvent pas prendre en charge cette fonctionnalité et peuvent retourner une erreur ou une chaîne vide.  
  
> [!NOTE]
>  **Utilisation du Service de données à distance** cette propriété n’est pas disponible sur un côté client **connexion** objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur et un exemple de propriétés DefaultDatabase (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider et DefaultDatabase, exemple de propriétés (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
