---
title: Paramètre Stream DCOM Format pour le Marshaling | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6b68071c379d61af64c71f5507281c127d9158a
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558336"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Définition du format pour le marshaling de flux DCOM
Un ordinateur client à l’aide de composants de RDS 1.5 ou une version antérieure n’est pas compatible avec un serveur à l’aide de composants de RDS 2.0 ou version ultérieure. Lorsque vous utilisez DCOM en tant que protocole sous-jacent, la prise en charge pour les services Bureau à distance 2.0 ou version ultérieure est plus efficace dans le transport [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objets. Si votre client exécute les composants de RDS 1.5 ou une version antérieure, vous pouvez définir votre serveur pour travailler avec la prise en charge des services Bureau à distance précédente (appelé RDS 1.0) ou la plus récente prise en charge de services Bureau à distance (RDS 2.0 ou version ultérieure). Définissez une des entrées de Registre suivantes :  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 -ou-  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```


