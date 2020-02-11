---
title: Enregistrement d’objets métier sur le client pour une utilisation avec DCOM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 31af4a68ec830a5fd514173c831ce3863fef7443
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922355"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Inscription d’objets métier sur le client en vue d’une utilisation avec DCOM
Les objets métier personnalisés doivent s’assurer que le côté client peut mapper leur nom de programme (ProgId) à un identificateur (CLSID) qui peut être utilisé sur DCOM. Pour cette raison, le ProgID de l’objet DCOM doit se trouver dans le registre côté client et être mappé à l’ID de classe de l’objet métier côté serveur. Pour les autres protocoles pris en charge (HTTP, HTTPs et in-process), cela n’est pas nécessaire.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Par exemple, si vous exposez un objet métier côté serveur appelé MyBObj avec un ID de classe spécifique, par exemple, « {00112233-4455-6677-8899-00AABBCCDDEE} », assurez-vous que les entrées suivantes sont ajoutées au registre côté client :  
  
```console
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


