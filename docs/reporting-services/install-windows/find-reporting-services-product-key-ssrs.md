---
title: Rechercher la clé de produit de SQL Server 2017 Reporting Services (SSRS) | Microsoft Docs
ms.date: 12/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 36460943b233f02e4d029b7865c7d7fa3844b488
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65502925"
---
# <a name="how-to-find-the-product-key-for-sql-server-2017-reporting-services"></a>Guide pratique pour rechercher la clé de produit de SQL Server 2017 Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)])

Découvrez comment trouver votre clé de produit SQL Server 2017 Reporting Services (SSRS) pour pouvoir installer votre serveur dans un environnement de production.

Pour trouver votre clé de produit, commencez par télécharger et exécuter le programme d’installation de SQL Server 2017.

1. Téléchargez SQL Server 2017 à partir d’une des sources suivantes :

    - Centre VLSC (Volume Licensing Service Center)
    - Abonnement MSDN
    - Version commercialisée (téléchargement à partir de Microsoft Store)

1. Exécutez le programme d’installation de SQL Server 2017 et copiez la clé préremplie :

    ![Copier la clé de produit SQL Server 2017](media/find-reporting-services-product-key-ssrs/ssrs-ss2017-copy-product-key.png)

1. [Exécutez le programme d’installation de Reporting Services](install-reporting-services.md) et collez la clé de produit :

     ![Coller la clé de produit](media/find-reporting-services-product-key-ssrs/ssrs-ssrs2017-paste-product-key.png)

Effectuez cette étape uniquement à la première installation de SSRS 2017. Vous n’avez normalement pas besoin d’entrer la clé de produit pour les mises à jour de maintenance.

## <a name="related-information"></a>Informations connexes

- Pour plus d’informations sur l’installation de SQL Server Reporting Services en mode natif, consultez [Installer le serveur de rapports Reporting Services en mode natif](install-reporting-services-native-mode-report-server.md). 

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

- Pour plus d’informations sur l’installation de SQL Server 2016 Reporting Services (et les versions antérieures) en mode intégré SharePoint, consultez [Installer le premier serveur de rapports en mode SharePoint](install-the-first-report-server-in-sharepoint-mode.md).

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

- [Installer SQL Server 2017 Reporting Services](install-reporting-services.md)
- D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
