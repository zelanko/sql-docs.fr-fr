---
title: IMise en œuvre d’une extension pour le traitement des données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8ebfc2d9704a1153f29fc8e97b4564d907e04938
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140231"
---
# <a name="implementing-a-data-processing-extension"></a>Implémentation d'une extension pour le traitement des données
  Les extensions pour le traitement des données dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] vous permettent de vous connecter à une source de données et de récupérer des données. Elles servent également de pont entre une source de données et un dataset Les extensions pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sont basées sur un sous-ensemble des interfaces de fournisseur de données [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble des extensions pour le traitement des données](data-processing-extensions-overview.md)  
 Explique comment écrire une extension personnalisée pour le traitement des données pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Préparation de la mise en œuvre d'une classe de commande pour une extension](preparing-to-implement-a-data-processing-extension.md)  
 Décrit les interfaces disponibles pour l'implémentation d'une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ainsi que l'implémentation d'une interface particulière.  
  
 [Création d'une bibliothèque d'extensions pour le traitement des données](creating-a-data-processing-extension-library.md)  
 Décrit l'assignation d'un espace de noms pour votre extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et la compilation de votre extension pour le traitement des données dans une DLL de bibliothèque.  
  
 [Mise en œuvre d'une classe de connexion pour une extension pour le traitement des données](implementing-a-connection-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’une connexion et comment implémenter votre propre classe **Connection** pour votre extension pour le traitement des données.  
  
 [Mise en œuvre d'une classe de commande pour une extension pour le traitement des données](implementing-a-command-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’une commande et comment implémenter votre propre classe **Command** pour votre extension pour le traitement des données.  
  
 [Mise en œuvre d'une classe DataReader pour une extension pour le traitement des données](implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’un lecteur de données et comment implémenter votre propre classe **DataReader** pour votre extension pour le traitement des données.  
  
 [Utilisation d'un jeu de données externe avec Reporting Services](using-an-external-dataset-with-reporting-services.md)  
 Décrit comment exposer vos objets **DataSet** personnalisés sur le serveur de rapports pour être exploité.  
  
 [Déploiement d'une extension pour le traitement des données](deploying-a-data-processing-extension.md)  
 Décrit comment déployer votre extension pour le traitement des données.  
  
 [Débogage du code des extensions pour le traitement des données](debugging-data-processing-extension-code.md)  
 Décrit comment déboguer le code dans vos extensions pour le traitement des données.  
  
 [Suppression d’une extension pour le traitement des données](removing-a-data-processing-extension.md)  
 Décrit comment supprimer une extension pour le traitement des données d'un serveur de rapports ou d'un Concepteur de rapports.  
  
 Pour un exemple d’extension pour le traitement des données totalement implémentée, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../reporting-services-extensions.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  