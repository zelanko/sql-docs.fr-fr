---
title: Objet DataFactory (RDSServer) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97597e15bc5cd8ee8d3008c97f3a4e8b07b2d43d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964325"
---
# <a name="datafactory-object-rdsserver"></a>DataFactory, objet (RDSServer)
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Cet objet métier par défaut côté serveur implémente des méthodes qui fournissent un accès en lecture/écriture aux données des sources de données spécifiées pour les applications côté client.  
  
 L’objet **RDSServer. DataFactory** est conçu comme un objet Automation côté serveur qui reçoit les demandes des clients. Dans une implémentation Internet, elle réside sur un serveur Web et est instanciée par le composant ADISAPI. L’objet **RDSServer. DataFactory** fournit un accès en lecture et en écriture aux sources de données spécifiées, mais ne contient pas de logique de validation ou de règle d’entreprise.  
  
 Si vous utilisez une méthode disponible à la fois dans **RDSServer. DataFactory** et dans [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) , le service de données distant utilise le **RDS. **Version de DataControl par défaut. La valeur par défaut est basée sur un scénario de programmation de base, où l’objet **RDSServer. DataFactory** sert d’objet métier générique côté serveur.  
  
 Si vous souhaitez que votre application Web gère le traitement côté serveur spécifique aux tâches, vous pouvez remplacer **RDSServer. DataFactory** par un objet métier personnalisé.  
  
 Vous pouvez créer des objets métier côté serveur qui appellent les méthodes **RDSServer. DataFactory** , telles que [query](../../../ado/reference/rds-api/query-method-rds.md) et [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md). Cela est utile si vous souhaitez ajouter des fonctionnalités à vos objets métier, mais tirer parti des technologies de services de données distantes existantes.  
  
 L’objet **DataFactory** n’est pas sûr pour les scripts qui s’exécutent côté client.  
  
 L’ID de classe de l’objet **RDSServer. DataFactory** est 9381D8F5-0288-11D0-9501-00AA00B911A5.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataFactory (exemple d’objet), Query (exemple de méthode) et CreateObject (exemple de méthode) (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


