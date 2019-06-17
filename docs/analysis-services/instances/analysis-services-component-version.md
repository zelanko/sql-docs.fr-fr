---
title: Vérifier la version de build de mise à jour cumulative de SQL Server Analysis Services | Microsoft Docs
ms.date: 07/11/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1da8384bb51360178e1735d13f6c6b706e8b7ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62659057"
---
# <a name="verify-analysis-services-cumulative-update-build-version"></a>Vérifier la version de build de la mise à jour cumulative d’Analysis Services

À compter de SQL Server 2017, le numéro de version de build Analysis Services et le numéro de version de build de moteur de base de données SQL Server ne correspondent pas. Tandis que Analysis Services et le moteur de base de données utilisent le même programme d’installation, les systèmes de build chaque utilisation sont distincts.

 Dans certains cas, il peut être nécessaire de vérifier si un package de build de mise à jour Cumulative (CU) a été appliqué et les composants Analysis Services ont été mis à jour. Vous pouvez vérifier en comparant les numéros de version de build des fichiers de composant Analysis Services installées sur votre ordinateur avec les numéros de version de build pour une CU particulier.

## <a name="verify-component-file-version"></a>Vérifier la version de fichier de composant

Pour vérifier la version du fichier de composant 

1. Accédez à [générer des versions de SQL Server 2017](https://support.microsoft.com/help/4047329). 
2. Dans **SQL Server 2017 mise à jour cumulative (CU) génère**, cliquez sur le **numéro Base de connaissances** pour la build que vous souhaitez vérifier.
3. Dans le **mise à jour Cumulative (#) pour SQL Server 2017** l’article, dans le **informations du package de mise à jour Cumulative** , développez **informations de fichier de package de mise à jour Cumulative**.
4. Dans le **SQL Server Analysis Services 2017** table, vérifiez la version de fichier pour le **msmdsrv.exe** fichier du composant. Si le CU a été appliqué, le numéro de version de fichier doit correspondre au fichier de msmdsrv.exe installé sur votre ordinateur.

## <a name="see-also"></a>Voir aussi  

[Installer des mises à jour de maintenance de SQL Server](../../database-engine/install-windows/install-sql-server-servicing-updates.md)  

[Centre de mises à jour pour Microsoft SQL Server](https://msdn.microsoft.com/library/ff803383.aspx)
  
  
