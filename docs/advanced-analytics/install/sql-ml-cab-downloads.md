---
title: CAB téléchargements pour les mises à jour cumulatives de SQL Server | Microsoft Docs
description: Téléchargements de fichier CAB pour SQL Server 2017 Machine Learning Services et SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 57481eaee3ee6de5816e69edda2936d4ee30fc49
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118282"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB télécharge les mises à jour cumulatives d’analytique en base de données de SQL Server instances

Les instances de SQL Server configurées pour l’analytique de la base de données incluent des fonctionnalités de R et Python fournis dans les fichiers CAB, installé et pris en charge par le biais le programme d’installation de SQL Server. 

Sur les serveurs connectés à internet, CAB mises à jour sont généralement appliquées via Windows Update. Déconnecté de serveurs doivent être mis à jour manuellement. Pour obtenir des instructions sur les installations en mode hors connexion, consultez [composants sans accès à internet d’apprentissage installer SQL Server](sql-ml-component-install-without-internet-access.md).

Cet article fournit des liens de téléchargement de fichiers CAB pour chaque mise à jour cumulative de SQL Server 2017 Machine Learning Services (R et Python) ou SQL Server 2016 R Services afin que vous pouvez mettre à jour manuellement les serveurs déconnectés d’internet. 

## <a name="prerequisites"></a>Prérequis

Démarrez avec une installation de base.

+ Sur SQL Server 2017 Machine Learning Services, la version initiale est l’installation de base. 
+ Sur SQL Server 2016 R Services, vous pouvez commencer avec la version initiale, le SP1 ou le SP2. 

Ensuite, appliquez [mises à jour cumulatives](https://support.microsoft.com/help/4047329) pour l’instance du moteur de base de données SQL Server.

Une fois que vous avez une installation de base et que vous avez appliqué les mises à jour cumulatives pour SQL Server, vous pouvez effectuer un [effectuer une installation intégrée de mise à niveau](sql-ml-component-install-without-internet-access.md#slipstream-upgrades) pour installer les fichiers CAB avec les fonctionnalités d’apprentissage automatique de mise à jour.

Fichiers CAB sont répertoriées dans l’ordre chronologique inverse. Lorsque vous téléchargez les fichiers CAB et les transférez vers l’ordinateur cible, les placer dans un dossier tel que **télécharge** ou le dossier %Temp% de l’utilisateur le programme d’installation.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CABs

Version  |Télécharger le lien  | Correctifs | 
---------|---------------|-------|
**[CU10](https://support.microsoft.com/help/4342123)** |  |  |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| |
R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Correctifs mineurs.|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| |
Serveur de Python    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Python rx_data_step perd l’ordre des lignes lorsque les doublons sont supprimés. <br/>Vitesse du Python ne parvient pas à l’obtention du type de données à partir d’un index columnstore cluster sous certaines conditions. <br/>Python retourne une table vide lorsque les colonnes contiennent toutes les valeurs null. |
**[CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur de Python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)]|
**[CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur de Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|
**[CU5](https://support.microsoft.com/help/4092643)** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur de Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**[CU4 ET VERSIONS ULTÉRIEURES](https://support.microsoft.com/help/4056498)** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
 Serveur de Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**[CU3](https://support.microsoft.com/help/4052987)** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur de Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**[CU1](https://support.microsoft.com/help/4038634)-[CU2](https://support.microsoft.com/help/4052574)** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur de Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**Version initiale** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Python de Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Serveur de Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CABs

Pour SQL Server 2016 R Services, les versions de ligne de base sont la version RTM ou une version service pack.

Version  |Télécharger le lien  |
---------|---------------|
**SQL Server 2016 SP2 CU1 à CU2**     |
Microsoft R Open     |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039)|
Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
**SQL Server 2016 SP1 CU4-CU10**     |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP1 CU1 à CU3**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)=
**SQL Server 2016 CU4-CU9**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU2-CU3**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 CU1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)

> [!NOTE]
> 
> Lorsque vous installez SQL Server 2016 SP1 CU4 ou SP1 CU5 hors connexion, téléchargez SRO_3.2.2.16000_1033.cab. Si vous avez téléchargé SRO_3.2.2.13000_1033.cab FWLINK 831785 comme indiqué dans la boîte de dialogue d’installation, renommez le fichier en tant que SRO_3.2.2.16000_1033.cab avant d’installer la mise à jour Cumulative.

Si vous souhaitez afficher le code source pour Microsoft R, il est disponible en téléchargement sous forme d’archive au format .tar : [programmes d’installation de télécharger R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

# <a name="see-also"></a>Voir aussi

[Installer les composants sans accès à internet d’apprentissage SQL Server](sql-ml-component-install-without-internet-access.md)
