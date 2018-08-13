---
title: CAB téléchargements pour les mises à jour cumulatives de SQL Server | Microsoft Docs
description: Téléchargements de fichier CAB pour SQL Server 2017 Machine Learning Services et SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a2893e976e64315a1aad742062e962269439b72
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566316"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB télécharge les mises à jour cumulatives d’analytique en base de données de SQL Server instances

Les instances de SQL Server configurées pour l’analytique de la base de données incluent des fonctionnalités de R et Python fournis dans les fichiers CAB, installé et pris en charge par le biais le programme d’installation de SQL Server. 

Sur les serveurs connectés à internet, CAB mises à jour sont généralement appliquées via Windows Update. Déconnecté de serveurs doivent être mis à jour manuellement. Cet article fournit des liens de téléchargement de fichiers CAB pour chaque mise à jour cumulative de SQL Server 2017 Machine Learning Services (R et Python) ou SQL Server 2016 R Services afin que vous pouvez mettre à jour manuellement les serveurs déconnectés d’internet. 

## <a name="prerequisites"></a>Prérequis

Démarrez avec une installation de base.

+ Sur SQL Server 2017 Machine Learning Services, la version initiale est l’installation de base. 

+ Sur SQL Server 2016 R Services, vous pouvez commencer avec la version initiale, le SP1 ou le SP2. 

Pour plus d’informations, consultez [composants sans accès à internet d’apprentissage installer SQL Server](sql-ml-component-install-without-internet-access.md).

Une fois que vous avez une installation de base, vous pouvez effectuer un [effectuer une installation intégrée de mise à niveau](sql-ml-component-install-without-internet-access.md#slipstream-upgrades) qui inclut les fichiers CAB avec les fonctionnalités d’apprentissage automatique mis à jour.

Fichiers CAB sont répertoriées dans l’ordre chronologique inverse. Lorsque vous téléchargez les fichiers CAB et les transférez vers l’ordinateur cible, les placer dans un dossier tel que **télécharge** ou le dossier %Temp% de l’utilisateur le programme d’installation.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CABs

Version  |Télécharger le lien  |
---------|---------|
**SQL Server 2017 CU8-CU9** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur Microsoft Python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)]|
**SQL Server 2017 CU6-CU7** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur Microsoft Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|
**SQL Server 2017 CU5** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur Microsoft Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**Cu4 et versions ultérieures SQL Server 2017** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur Microsoft Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**SQL Server 2017 CU3** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur Microsoft Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 CU1 à CU2** |
Microsoft R Open     |aucune modification ; utiliser le précédent [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Python de Microsoft Open     |aucune modification ; utiliser le précédent [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Serveur Microsoft Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**Version initiale de SQL Server 2017** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Python de Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Serveur Microsoft Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


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
