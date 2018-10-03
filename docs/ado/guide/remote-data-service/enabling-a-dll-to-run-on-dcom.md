---
title: Configuration d’une DLL pour son exécution sur DCOM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95bfd4d5f5c5dac4f5ee4a74369e68bd40f8f698
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788847"
---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Configuration d’une DLL pour s’exécuter sur DCOM
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Les étapes suivantes décrivent comment activer une .dll d’objet métier à utiliser DCOM et Microsoft Internet Information Services (HTTP) via les Services de composants.  
  
1.  Créer un nouveau package vide dans le composant logiciel enfichable MMC Services de composants.  
  
     Vous allez utiliser le composant logiciel enfichable MMC Services de composants pour créer un package et ajouter la DLL dans ce package. Le fichier .dll est ainsi accessible via DCOM, mais il supprime l’accessibilité via IIS. (Si vous recherchez dans le Registre pour le fichier .dll, le **Inproc** clé est maintenant vide ; définissant l’attribut d’Activation, expliqué plus loin dans cette rubrique, ajoute une valeur dans le **Inproc** clé.)  
  
2.  Installer un objet métier dans le package.  
  
     -ou-  
  
     Importer le [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objet dans le package.  
  
3.  Définissez l’attribut d’Activation pour le package à **dans le processus du créateur** (application de bibliothèque).  
  
     Pour rendre le fichier .dll accessibles via DCOM et IIS sur le même ordinateur, vous devez définir l’attribut du composant d’Activation dans le composant logiciel enfichable MMC Services de composants. Une fois que vous définissez l’attribut sur **dans le processus du créateur**, vous remarquerez qu’un **Inproc** clé de serveur dans le Registre a été ajoutée à la DLL de substitution pointe vers un composant des Services.  
  
 Pour plus d’informations sur les Services de composants (ou Service Microsoft Transaction, si vous utilisez Windows NT) et comment effectuer ces étapes, visitez le site Web de Microsoft Transaction Server.


