---
title: Définition du format de marshaling de flux DCOM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
author: rothja
ms.author: jroth
ms.openlocfilehash: f3e7dd82d54b20ccceec73c0917f4f81c3cf16dd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758955"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Définition du format pour le marshaling de flux DCOM
Un ordinateur client utilisant des composants de RDS 1,5 ou version antérieure n’est pas compatible avec un serveur utilisant des composants de RDS 2,0 ou version ultérieure. Lors de l’utilisation de DCOM comme protocole sous-jacent, la prise en charge de RDS 2,0 ou version ultérieure est plus efficace dans le transport d’objets [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) . Si votre client exécute des composants de RDS 1,5 ou version antérieure, vous pouvez configurer votre serveur pour qu’il fonctionne avec la prise en charge de RDS précédente (appelée RDS 1,0) ou la prise en charge de RDS la plus récente (appelée RDS 2,0 ou version ultérieure). Définissez l’une des entrées de Registre suivantes :  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 -ou-  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```


