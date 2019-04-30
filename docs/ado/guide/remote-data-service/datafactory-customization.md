---
title: Personnalisation de DataFactory | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31434e08443bc533c7e2ae14ed70d6962aea04cf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214762"
---
# <a name="datafactory-customization"></a>Personnalisation de DataFactory
Service de données à distance (RDS) fournit un moyen d’effectuer facilement accès aux données dans un système à trois niveaux client/serveur. Un contrôle de données client spécifie des paramètres de chaîne de connexion et de commande pour effectuer une requête sur une source de données distante ou une chaîne de connexion et [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) paramètres nécessaires pour effectuer une mise à jour de l’objet.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Les paramètres sont passés à un programme de serveur qui exécute l’opération d’accès aux données sur la source de données distante. Services Bureau à distance fournit un programme serveur par défaut le [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objet. Le **RDSServer.DataFactory** objet renvoie aucune **Recordset** objet produit par une requête au client.  
  
 Toutefois, le **RDSServer.DataFactory** est limité à la réalisation des requêtes et des mises à jour. Elle ne peut pas effectuer de valider ou d’un traitement sur les chaînes de connexion ou de commande.  
  
 Avec ADO, vous pouvez spécifier que le **DataFactory** fonctionnent conjointement avec un autre type de programme serveur appelé un *gestionnaire*. Le gestionnaire peut modifier les chaînes de commande et de connexion du client avant d’être utilisés pour accéder à la source de données. En outre, le gestionnaire peut appliquer des droits d’accès qui régissent la capacité du client pour lire et écrire des données dans la source de données.  
  
 Les paramètres que le Gestionnaire utilise pour modifier les paramètres de client et les droits d’accès sont spécifiés dans les sections d’un fichier de personnalisation.  
  
 Les rubriques suivantes fournissent plus d’informations sur la personnalisation de la **DataFactory** objet.  
  
-   [Présentation du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [Fichier de personnalisation, section connect](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [Fichier de personnalisation, section SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [Fichier de personnalisation, section UserList](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [Fichier de personnalisation, section Logs](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [Paramètres client obligatoires](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


