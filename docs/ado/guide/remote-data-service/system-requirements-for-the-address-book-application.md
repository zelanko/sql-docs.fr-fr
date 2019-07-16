---
title: Configuration système requise pour l’adresse du carnet d’Application | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2450cc97229a6629d4c2895f3960e3033d129789
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922035"
---
# <a name="system-requirements-for-the-address-book-application"></a>Configuration système exigée pour l’application Carnet d’adresses
Pour configurer l’exemple d’application Carnet d’adresses, vous devez remplir les conditions de logiciels et de la base de données suivantes :  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="software-requirements"></a>Configuration logicielle  
 La configuration logicielle requise de l’ordinateur serveur pour l’exécution de cette application Web est les suivantes :  
  
-   Microsoft Windows NT® Server 4.0 avec Service Pack 3 ou version ultérieure, ou Microsoft Windows® 2000 Server.  
  
-   Microsoft Internet Information Services (IIS) version 3.0 ou version ultérieure, avec Active Server Pages.  
  
 La configuration logicielle requise de l’ordinateur client pour l’exécution de cette application Web est les suivantes :  
  
-   Microsoft Internet Explorer 4.0 ou version ultérieure.  
  
-   Microsoft Windows NT 4.0 Workstation ou Server, Windows 2000 ou Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Configuration requise pour la base de données  
 Pour utiliser cet exemple, vous devez disposer de :  
  
-   Un serveur de version 6.5 ou ultérieure de la base de données de la version de Microsoft® SQL Server opérationnel.  
  
-   Privilèges pour créer la base de données et le remplir avec les exemples de données.  
  
-   Vérification des données remplies via Enterprise Manager ou les utilitaires ISQL (appelé analyseur de requêtes dans SQL Server 7.0).  
  
 Si vous n’avez pas de privilèges, votre administrateur de base de données peut avoir besoin configurer le système et donnent accès à la base de données ou de configurer la base de données pour vous.  
  
## <a name="see-also"></a>Voir aussi  
 [Le Script SQL carnet d’adresse en cours d’exécution](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Exécution de l’exemple d’application Carnet d’adresses](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


