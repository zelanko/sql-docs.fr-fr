---
description: OriginalValue, propriété (ADO)
title: OriginalValue, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
author: rothja
ms.author: jroth
ms.openlocfilehash: ab73e79f86ac1e504322a0606ee3839997ce5811
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990210"
---
# <a name="originalvalue-property-ado"></a>OriginalValue, propriété (ADO)
Indique la valeur d’un [champ](./field-object.md) qui existait dans l’enregistrement avant toute modification.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne une valeur de **type Variant** qui représente la valeur d’un champ avant toute modification.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **OriginalValue** pour retourner la valeur de champ d’origine d’un champ de l’enregistrement actif.  
  
 En *mode de mise à jour immédiate* (dans lequel le fournisseur enregistre les modifications apportées à la source de données sous-jacente après l’appel de la méthode [Update](./update-method.md) ), la propriété **OriginalValue** retourne la valeur de champ qui existait avant toute modification (autrement dit, depuis le dernier appel de la méthode **Update** ). Il s’agit de la même valeur que celle utilisée par la méthode [CancelUpdate](./cancelupdate-method-ado.md) pour remplacer la propriété [value](./value-property-ado.md) .  
  
 En *mode de mise à jour par lot* (dans lequel le fournisseur met en cache plusieurs modifications et les écrit dans la source de données sous-jacente uniquement lorsque vous appelez la méthode [UpdateBatch](./updatebatch-method.md) ), la propriété **OriginalValue** retourne la valeur de champ qui existait avant toute modification (autrement dit, depuis le dernier appel de la méthode **UpdateBatch** ). Il s’agit de la même valeur que celle utilisée par la méthode [CancelBatch](./cancelbatch-method-ado.md) pour remplacer la propriété **value** . Lorsque vous utilisez cette propriété avec la propriété [UnderlyingValue](./underlyingvalue-property.md) , vous pouvez résoudre les conflits qui résultent des mises à jour par lots.  
  
## <a name="record"></a>Enregistrement  
 Pour les objets [Record](./record-object-ado.md) , la propriété **OriginalValue** est vide pour les champs ajoutés avant l’appel de la méthode [Update](./update-method.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](./field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, exemples de propriétés (VB)](./originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, exemples de propriétés (VC + +)](./originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue, propriété](./underlyingvalue-property.md)