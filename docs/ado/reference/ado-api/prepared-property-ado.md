---
title: Prepared, propriété (ADO) | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917590"
---
# <a name="prepared-property-ado"></a>Prepared, propriété (ADO)
Indique s’il faut enregistrer une version compilée d’une [commande](../../../ado/reference/ado-api/command-object-ado.md) avant l’exécution.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur **booléenne** qui, si elle a la valeur **true**, indique que la commande doit être préparée.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **Prepared** pour que le fournisseur enregistre une version préparée (ou compilée) de la requête spécifiée dans la propriété [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) avant la première exécution d’un objet [Command](../../../ado/reference/ado-api/command-object-ado.md) . Cela peut ralentir la première exécution d’une commande, mais une fois que le fournisseur compile une commande, le fournisseur utilise la version compilée de la commande pour toutes les exécutions ultérieures, ce qui entraîne une amélioration des performances.  
  
 Si la propriété a la **valeur false**, le fournisseur exécutera directement l’objet de **commande** sans créer une version compilée.  
  
 Si le fournisseur ne prend pas en charge la préparation de la commande, il peut retourner une erreur lorsque cette propriété a la valeur **true**. Si le fournisseur ne retourne pas d’erreur, il ignore simplement la demande de préparation de la commande et affecte la **valeur false**à la propriété **Prepared** .  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prepared, exemple de propriété (VB)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Prepared, exemple de propriété (VC++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
