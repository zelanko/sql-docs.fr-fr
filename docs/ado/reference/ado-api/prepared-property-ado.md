---
title: Préparé, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Prepared
helpviewer_keywords:
- Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ee7a94a06aa574c84c01cb8b9d05ebfcdf327d44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917590"
---
# <a name="prepared-property-ado"></a>Prepared, propriété (ADO)
Indique s’il faut enregistrer une version compilée d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) avant l’exécution.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **booléenne** valeur qui, si la valeur **True**, indique que la commande doit être préparée.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **Prepared** propriété pour que le fournisseur enregistre une version préparée (ou compilée) de la requête spécifiée dans le [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété avant un [commande](../../../ado/reference/ado-api/command-object-ado.md) l’objet première exécution. Cela peut ralentir une première exécution, mais une fois que le fournisseur compile une commande, le fournisseur utilisera la version compilée de la commande pour des exécutions suivantes, ce qui entraînent une amélioration des performances.  
  
 Si la propriété est **False**, le fournisseur exécute le **commande** objet directement sans créer une version compilée.  
  
 Si le fournisseur ne prend pas en charge la préparation de la commande, elle peut retourner une erreur lors de cette propriété est définie sur **True**. Si le fournisseur ne retourne pas d’erreur, il ignore simplement la demande de préparation de la commande et les affecte le **Prepared** propriété **False**.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prepared, propriété, exemple (VB)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Prepared, exemple de propriété (VC++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
