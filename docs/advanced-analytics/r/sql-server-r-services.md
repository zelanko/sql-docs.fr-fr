---
title: R services en SQL Server 2016
description: R en SQL Server pour les tâches R intégrées sur les données relationnelles, notamment la science des données et la modélisation statistique, l’analyse prédictive, la visualisation des données et bien plus encore.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/10/2018
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: e849140125ba39c7c1d8601c5ef32880a9d633ac
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344838"
---
# <a name="r-services-in-sql-server-2016"></a>R services en SQL Server 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R services est un module complémentaire d’une instance de moteur de base de données SQL Server 2016, utilisé pour exécuter du code R et des fonctions sur SQL Server. Le code s’exécute dans une infrastructure d’extensibilité, isolée des processus du moteur de base, mais entièrement disponible pour les données relationnelles en tant que procédures stockées, comme script T-SQL contenant des instructions R ou comme code R contenant T-SQL. 

R services comprend une distribution de base de R, superposée aux packages Enterprise R de Microsoft pour vous permettre de charger et traiter de grandes quantités de données sur plusieurs cœurs et d’agréger les résultats dans une sortie consolidée unique. Les fonctions et algorithmes R de Microsoft sont conçus pour la mise à l’échelle et l’utilitaire: la diffusion d’analyses prédictives, de modélisations statistiques, de visualisations de données et d’algorithmes de Machine Learning de pointe dans un produit de serveur commercial conçu et pris en charge par Microsoft. 

Les bibliothèques R incluent [**RevoScaleR**](ref-r-revoscaler.md), [**MicrosoftML (R)** ](ref-r-microsoftml.md)et d’autres. Étant donné que R services est intégré au moteur de base de données, vous pouvez conserver les analyses proches des données et éliminer les coûts et les risques de sécurité liés au déplacement des données.

> [!Note]
> R services a été renommé dans SQL Server 2017 et versions ultérieures pour [SQL Server machine learning services](../what-is-sql-server-machine-learning.md), reflétant l’ajout de Python.

## <a name="components"></a>Composants

SQL Server 2016 est R uniquement. Le tableau suivant décrit les fonctionnalités de SQL Server 2016.

| Composant | Description |
|-----------|-------------|
| Service SQL Server Launchpad | Service qui gère les communications entre les runtimes R externes et l’instance SQL Server. |
| Packages R | [**RevoScaleR**](ref-r-revoscaler.md) est la bibliothèque principale de R. les fonctions évolutives dans cette bibliothèque sont parmi les plus couramment utilisées. La transformation et la manipulation des données, le résumé statistique, la visualisation et de nombreuses formes de modélisation et d’analyse sont rendues possibles avec ces bibliothèques. De plus, les fonctions de ces bibliothèques répartissent automatiquement les charges de travail entre les cœurs disponibles pour un traitement parallèle, avec la possibilité de travailler sur des blocs de données qui sont coordonnés et gérés par le moteur de calcul.  <br/>[**MicrosoftML (R)** ](ref-r-microsoftml.md) ajoute des algorithmes machine learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments. <br/>[**sqlRUtils**](ref-r-sqlrutils.md) fournit des fonctions d’assistance pour placer des scripts R dans une procédure stockée T-SQL, inscrire une procédure stockée avec une base de données et exécuter la procédure stockée à partir d’un environnement de développement R.<br/>[**olapr**](ref-r-olapr.md) est destiné à la spécification de requêtes MDX dans R.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) est la distribution Open source de Microsoft de R. Le package et l’interpréteur sont inclus. Utilisez toujours la version de MRO installée par le programme d’installation de. |
| Outils R | Les fenêtres de console R et les invites de commande sont des outils standard dans une distribution R.  |
| Exemples et scripts R |  Les packages R et RevoScaleR Open source incluent des jeux de données intégrés qui vous permettent de créer et d’exécuter un script à l’aide de données pré-installées |
| Modèles pré-formés dans R | Des modèles préformés sont créés pour des cas d’usage spécifiques et gérés par l’équipe d’ingénierie de science des données chez Microsoft. Vous pouvez utiliser les modèles préformés tels quels pour noter des sentiments positifs et négatifs dans du texte, ou pour détecter des fonctionnalités dans des images, en utilisant de nouvelles entrées de données que vous fournissez. Les modèles s’exécutent dans R services, mais ne peuvent pas être installés par le biais du programme d’installation de SQL Server. Pour plus d’informations, consultez [installer des modèles de machine learning pré-formés sur SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-r-services"></a>Utilisation de R services

Les développeurs et les analystes ont souvent du code s’exécutant sur une instance de SQL Server locale. En ajoutant Machine Learning Services et en activant l’exécution de scripts externes, vous avez la possibilité d’exécuter du code R dans des SQL Server modales: l’encapsulation de script dans des procédures stockées, le stockage de modèles dans une table SQL Server ou la combinaison de fonctions T-SQL et R dans les requêtes.

L’approche la plus courante pour l’analyse dans la base de données consiste à utiliser [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), en transmettant le script R en tant que paramètre d’entrée.

Les interactions client-serveur classiques sont une autre approche. À partir de n’importe quelle station de travail cliente dotée d’un IDE, vous pouvez installer [Microsoft R client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client), puis écrire du code qui pousse l’exécution (appelée *contexte de calcul distant*) vers des données et des opérations vers un SQL Server distant. 

Enfin, si vous utilisez un [serveur autonome](r-server-standalone.md) et l’édition développeur, vous pouvez créer des solutions sur une station de travail cliente à l’aide des mêmes bibliothèques et interpréteurs, puis déployer le code de production sur SQL Server machine learning services (dans la base de données). 

## <a name="how-to-get-started"></a>Prise en main

Commencez par le programme d’installation, attachez les fichiers binaires à votre outil de développement favori et écrivez votre premier script.

**Étape 1 :** Installez et configurez le logiciel. 

+ [Installer SQL Server 2016 R services (en base de données)](../install/sql-r-services-windows-install.md)

**Étape 2 :** Profitez d’une expérience pratique en utilisant l’un des didacticiels suivants:

+ [Tutoriel : En savoir plus sur l’analytique de base de données à l’aide de R](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Tutoriel : Procédure pas à pas de bout en bout avec R](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**Étape 3 :** Ajoutez vos packages R préférés et utilisez-les avec des packages fournis par Microsoft

+ [Gestion des packages R pour SQL Server](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>Voir aussi

 [Installer SQL Server 2016 R services](../install/sql-r-services-windows-install.md)
