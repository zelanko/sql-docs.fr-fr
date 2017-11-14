---
title: "Propriété DefaultDatabase | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a95c2f237a47e5908c5218d45c7d1fa74f87dff9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
 [Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur et un exemple de propriétés DefaultDatabase (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Fournisseur et un exemple de propriétés DefaultDatabase (VC ++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   

