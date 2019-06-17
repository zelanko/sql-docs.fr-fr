---
title: Téléchargements de fichier CAB pour les mises à jour cumulatives de SQL Server - SQL Server Machine Learning
description: R et Python CAB et package téléchargements pour SQL Server 2017 Machine Learning Services et SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 3c5c27186969db01cc90fa43a6cf4ec2774ab051
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66403239"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB télécharge les mises à jour cumulatives d’analytique en base de données de SQL Server instances

Les instances de SQL Server qui sont configurés pour la base de données analytique incluent des fonctionnalités de R et Python. Ces fonctionnalités sont livrés dans les fichiers CAB, installé et traitées via le programme d’installation de SQL Server. Sur les appareils connectés à internet, CAB mises à jour sont généralement appliquées via Windows Update. Sur les serveurs déconnectés, les fichiers CAB doivent être téléchargées et appliquées manuellement. 

Cet article fournit des liens de téléchargement pour les fichiers CAB pour chaque mise à jour cumulative. Des liens sont fournis pour SQL Server 2017 Machine Learning Services (R et Python), ainsi que SQL Server 2016 R Services. Pour plus d’informations sur les installations en mode hors connexion, consultez [composants sans accès à internet d’apprentissage installer SQL Server](sql-ml-component-install-without-internet-access.md#apply-cu).

## <a name="prerequisites"></a>Prérequis

Démarrez avec une installation de base.

+ Sur SQL Server 2017 Machine Learning Services, la version initiale est l’installation de base. 
+ Sur SQL Server 2016 R Services, vous pouvez commencer avec la version initiale, le SP1 ou le SP2. 

Vous pouvez également appliquer des mises à jour cumulatives pour un serveur autonome.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CABs

Fichiers CAB sont répertoriées dans l’ordre chronologique inverse. Lorsque vous téléchargez les fichiers CAB et les transférez vers l’ordinateur cible, les placer dans un dossier tel que **télécharge** ou le dossier %Temp% de l’utilisateur le programme d’installation.

|Version  |Composant | Télécharger le lien  | Problèmes résolus | 
|---------|----------|----------------|------------------|
|**[SQL Server 2017 CU14](https://support.microsoft.com/help/4484710/)-[CU15](https://support.microsoft.com/help/4498951/)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073898&clcid=1033)| Les fichiers binaires dans le package sont maintenant signés. |
| | R Server      |[SRS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2069739&clcid=1033)| Les fichiers binaires dans le package sont maintenant signés. |
| | Python de Microsoft Open     | [SPO_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073897&clcid=1033)| Les fichiers binaires dans le package sont maintenant signés. |
| | Serveur de Python    |[SPS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2071421&clcid=1033)| Les fichiers binaires dans le package sont maintenant signés.  |
|**[SQL Server 2017 CU13](https://support.microsoft.com/help/4466404)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification à partir de versions précédentes. |
| | R Server      |[SRS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038263&clcid=1033)| Contient un correctif pour la mise à niveau un [mis en œuvre de R Server autonome](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), comme installé via le programme d’installation de SQL Server. Utilisez les fichiers CAB CU13 et suivez [ces instructions](sql-machine-learning-standalone-windows-install.md#apply-cu) pour appliquer la mise à jour. |
| | Python de Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification à partir de versions précédentes. |
| | Serveur de Python    |[SPS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038197&clcid=1033)| Contient un correctif pour la mise à niveau un [mis en œuvre de Python serveur autonome](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), comme installé via le programme d’installation de SQL Server. Utilisez les fichiers CAB CU13 et suivez [ces instructions](sql-machine-learning-standalone-windows-install.md#apply-cu) pour appliquer la mise à jour. |
|**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)-[CU12](https://support.microsoft.com/help/4464082)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification à partir de versions précédentes. |
| | R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Correctifs mineurs.|
| | Python de Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification à partir de versions précédentes. |
| | Serveur de Python    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Python rx_data_step perd l’ordre des lignes lorsque les doublons sont supprimés. <br/>Vitesse du échoue la détection de type de données sur un index columnstore. <br/>Retourne une table vide lorsque les colonnes contiennent toutes les valeurs null. |
|**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification à partir de versions précédentes. |
| | R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
| | Python de Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification à partir de versions précédentes. |
| | Serveur de Python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
|**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification à partir de versions précédentes. |
| | R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
| | Python de Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification à partir de versions précédentes. |
| | Serveur de Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| Types de données DateTime dans la requête SPEES.<br/>amélioration des messages d’erreur dans microsoftml lors modèles préentraînés sont manquants.<br/> Correctifs de revoscalepy transformer les fonctions et variables.|
|**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification à partir de versions précédentes. |
| | R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| Erreurs de long chemin d’accès relatif dans rxInstallPackages.<br/>Connexions dans un bouclage pour RxExec.
| | Python de Microsoft Open    | Aucune modification à partir de versions précédentes. |
| | Serveur de Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>Connexions dans un bouclage pour rx_exec.
|**[SQL Server 2017 CU4](https://support.microsoft.com/help/4056498)** |  |   |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification à partir de versions précédentes. |
| | R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
| | Python de Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification à partir de versions précédentes. |
| |  Serveur de Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
|**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |  |
| | Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
| | R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
| | Python de Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification à partir de versions précédentes. |
| | Serveur de Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| Sérialisation dans revoscalepy, de modèle de Python à l’aide de la [rx_serialize_model fonction](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/>[Notation native](../sql-native-scoring.md) prise en charge, ainsi que des améliorations apportées aux [de score en temps réel](../real-time-scoring.md). 
|**[SQL Server 2017 CU1](https://support.microsoft.com/help/4038634)-[CU2](https://support.microsoft.com/help/4052574)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| Aucune modification à partir de versions précédentes. |
| | R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
| | Python de Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification à partir de versions précédentes. | 
| | Serveur de Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | Ajoute rx_create_col_info pour retourner des informations de schéma. <br/>Améliorations apportées aux [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) pour prendre en charge les scénarios parallèles à l’aide de la `RxLocalParallel` contexte de calcul.|
|**Version initiale** |  |  |
| | Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
| | R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
| | Python de Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
| | Serveur de Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CABs

Pour SQL Server 2016 R Services, les versions de ligne de base sont la version RTM ou une version service pack.

|Version  |Télécharger le lien  |
|---------|---------------|
|**SQL Server 2016 SP2 CU6**     |
|Microsoft R Open     |[SRO_3.2.2.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079936&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079933&clcid=1033)|
|**SQL Server 2016 SP2 CU1-CU5**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
|**SQL Server 2016 SP2**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)|
|**SQL Server 2016 SP1 CU14**     |
|Microsoft R Open     |[SRO_3.2.2.16100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2080130&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.17200_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079935&clcid=1033)|
|**SQL Server 2016 SP1 CU1-CU13**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
|**SQL Server 2016 SP1**     |
|Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)|
|Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)|
|**SQL Server 2016 CU4-CU9**     |
|Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
|Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
|**SQL Server 2016 CU2-CU3**     |
|Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)|
|Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)|
|**SQL Server 2016 CU1**     |
|Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)|
|Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)|
|**SQL Server 2016 RTM**     |
|Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)|
|Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)|

> [!NOTE]
> 
> Lorsque vous installez SQL Server 2016 SP1 CU4 ou SP1 CU5 hors connexion, téléchargez SRO_3.2.2.16000_1033.cab. Si vous avez téléchargé SRO_3.2.2.13000_1033.cab FWLINK 831785 comme indiqué dans la boîte de dialogue d’installation, renommez le fichier en tant que SRO_3.2.2.16000_1033.cab avant d’installer la mise à jour Cumulative.

Si vous souhaitez afficher le code source pour Microsoft R, il est disponible en téléchargement sous forme d’archive au format .tar : [Téléchargez les programmes d’installation de R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

## <a name="see-also"></a>Voir aussi

[Appliquer des mises à jour cumulatives sur les ordinateurs sans accès à internet](sql-ml-component-install-without-internet-access.md#apply-cu)

[Appliquer des mises à jour cumulatives sur des ordinateurs disposant d’une connectivité internet](sql-ml-component-install-without-internet-access.md#apply-cu)

[Appliquer des mises à jour cumulatives pour un serveur autonome](sql-machine-learning-standalone-windows-install.md#apply-cu)
