---
title: Exécution d’objets métier dans les Services de composants | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87eab0ac5611b437f6e0cbe1957a4d6e8652c4b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922276"
---
# <a name="running-business-objects-in-component-services"></a>Exécution d’objets métier dans les services de composants
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Objets métier peuvent être des fichiers exécutables (.exe) ou des bibliothèques de liens dynamiques (.dll). La configuration que vous utilisez pour exécuter l’objet métier varie selon que l’objet est un fichier .dll ou .exe :  
  
-   Les objets métier créés en tant que fichiers .exe peuvent être appelés via DCOM. Si ces objets métier sont utilisés par le biais d’Internet Information Services (IIS), ils sont susceptibles d’être supplémentaires de marshaling de données, ce qui ralentissent les performances du client.  
  
-   Les objets métier créés comme fichiers .dll peuvent être utilisés par IIS et donc également par HTTP. Elles peuvent également servir via DCOM uniquement par le biais de Services de composants ou via Microsoft Transaction Server, si vous utilisez Windows NT. DLL de l’objet métier doivent être inscrites sur l’ordinateur de serveur IIS pour y accéder via IIS. Pour plus d’informations sur la configuration d’une DLL pour s’exécuter sur DCOM, consultez la section [l’activation d’une DLL pour son exécution sur DCOM](../../../ado/guide/remote-data-service/enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Lorsque les objets métier sur la couche intermédiaire sont implémentés en tant que composants des Services de composants à l’aide de **GetObjectContext**, **SetComplete**, et **SetAbort**, l’entreprise les objets peuvent utiliser les Services de composants (ou MTS, si vous utilisez Windows NT) des objets de contexte pour maintenir leur état entre plusieurs appels clients. Ce scénario est possible avec DCOM, qui est généralement implémentée entre les clients approuvés et des serveurs dans un intranet. Dans ce cas, le [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet et [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) méthode côté client sont remplacés par l’objet de contexte de transaction et **CreateInstance** (méthode), qui sont fournies par le **ITransactionContext** interface et implémenté par les Services de composants.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


