---
title: "Configuration système requise pour l’adresse du carnet d’Application | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 070c809c23fcd70c5048e70f61ac74ad4bc7ce4b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="system-requirements-for-the-address-book-application"></a>Configuration système requise pour l’Application de carnet d’adresses
Pour configurer l’exemple d’application de carnet d’adresses, vous devez remplir les conditions de logiciels et de la base de données suivantes :  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="software-requirements"></a>Configuration logicielle  
 La configuration logicielle requise de l’ordinateur serveur pour l’exécution de cette application Web est les suivantes :  
  
-   Microsoft Windows NT® Server 4.0 avec Service Pack 3 ou version ultérieure, ou Microsoft Windows® 2000 Server.  
  
-   Microsoft Internet Information Services (IIS) version 3.0 ou version ultérieure, avec Active Server Pages.  
  
 La configuration logicielle requise de l’ordinateur client pour l’exécution de cette application Web est les suivantes :  
  
-   Microsoft Internet Explorer 4.0 ou version ultérieure.  
  
-   Microsoft Windows NT 4.0 Workstation ou Server, Windows 2000 ou Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Configuration requise pour la base de données  
 Pour utiliser cet exemple, vous devez :  
  
-   Un fonctionnement Microsoft® SQL Server version 6.5 ou ultérieure de base de données de serveur.  
  
-   Privilèges pour créer la base de données et le remplir avec les exemples de données.  
  
-   Vérification des données remplies via Enterprise Manager ou les utilitaires ISQL (appelé analyseur de requêtes dans SQL Server 7.0).  
  
 Si vous ne disposez pas de privilèges, votre administrateur de base de données devrez peut-être configurer le système et donner accès à la base de données ou de configurer la base de données pour vous.  
  
## <a name="see-also"></a>Voir aussi  
 [Le Script SQL de carnet d’adresses en cours d’exécution](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Exécution de l’exemple d’application Carnet d’adresses](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)



