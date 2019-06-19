---
title: DefaultDatabase, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2eb89353c29ae58194f89b48502f0a9cc5522b58
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695445"
---
# <a name="defaultdatabase-property"></a>DefaultDatabase, propriété
Indique la base de données par défaut pour un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur que prend le nom d’une base de données disponible à partir du fournisseur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **DefaultDatabase** propriété pour définir ou retourner le nom de la base de données par défaut sur un spécifique **connexion** objet.  
  
 S’il existe une base de données par défaut, les chaînes SQL peuvent utiliser une syntaxe non qualifiée pour accéder aux objets dans cette base de données. Pour accéder aux objets dans une base de données autre que celui spécifié dans le **DefaultDatabase** propriété, vous devez qualifier les noms d’objets avec le nom de la base de données souhaitée. Lors de la connexion, le fournisseur écrit les informations de base de données par défaut pour le **DefaultDatabase** propriété. Certains fournisseurs n'autorisent qu’une seule base de données par connexion, auquel cas vous ne pouvez pas modifier le **DefaultDatabase** propriété.  
  
 Certaines sources de données et les fournisseurs ne peuvent pas prendre en charge cette fonctionnalité et peuvent retourner une erreur ou une chaîne vide.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** cette propriété n’est pas disponible sur une côté client **connexion** objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Provider et DefaultDatabase propriétés exemple (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider et DefaultDatabase, exemple de propriétés (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
