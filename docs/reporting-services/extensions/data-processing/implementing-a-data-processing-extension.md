---
title: "Implémentation d’une Extension de traitement de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 1497690ebccc010601542308747240d0e91d89db
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-data-processing-extension"></a>Implémentation d'une extension pour le traitement des données
  Les extensions pour le traitement des données dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] vous permettent de vous connecter à une source de données et de récupérer des données. Elles servent également de pont entre une source de données et un dataset [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]extensions pour le traitement de données sont basées sur un sous-ensemble de la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] interfaces de fournisseur de données.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble des Extensions de traitement des données](../../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)  
 Explique comment écrire une extension personnalisée pour le traitement des données pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Préparation à l’implémentation d’une Extension de traitement de données](../../../reporting-services/extensions/data-processing/preparing-to-implement-a-data-processing-extension.md)  
 Décrit les interfaces disponibles pour l'implémentation d'une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ainsi que l'implémentation d'une interface particulière.  
  
 [Création d’une bibliothèque d’Extension de traitement des données](../../../reporting-services/extensions/data-processing/creating-a-data-processing-extension-library.md)  
 Décrit l'assignation d'un espace de noms pour votre extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et la compilation de votre extension pour le traitement des données dans une DLL de bibliothèque.  
  
 [Implémentation d’une classe de connexion pour une Extension de traitement de données](../../../reporting-services/extensions/data-processing/implementing-a-connection-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’une connexion et comment implémenter votre propre **connexion** classe pour votre extension pour le traitement des données.  
  
 [Implémentation d’une classe de commande pour une Extension de traitement de données](../../../reporting-services/extensions/data-processing/implementing-a-command-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’une commande et comment implémenter votre propre **commande** classe pour votre extension pour le traitement des données.  
  
 [Implémentation d’une classe DataReader pour une Extension de traitement de données](../../../reporting-services/extensions/data-processing/implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’un lecteur de données et comment implémenter votre propre **DataReader** classe pour votre extension pour le traitement des données.  
  
 [À l’aide d’un Dataset externe avec Reporting Services](../../../reporting-services/extensions/data-processing/using-an-external-dataset-with-reporting-services.md)  
 Décrit comment exposer votre personnalisé **DataSet** objets au serveur de rapports pour la consommation.  
  
 [Déploiement d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
 Décrit comment déployer votre extension pour le traitement des données.  
  
 [Débogage du Code d’Extension de traitement des données](../../../reporting-services/extensions/data-processing/debugging-data-processing-extension-code.md)  
 Décrit comment déboguer le code dans vos extensions pour le traitement des données.  
  
 [Suppression d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/removing-a-data-processing-extension.md)  
 Décrit comment supprimer une extension pour le traitement des données d'un serveur de rapports ou d'un Concepteur de rapports.  
  
 Pour voir un exemple d’une extension de traitement des données totalement implémenté, [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

