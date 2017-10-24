---
title: "Interopérabilité de Python | Documents Microsoft"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32762183ff5273998848978238788cc830319b91
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="python-interoperability"></a>Interopérabilité de Python

Cette rubrique décrit les composants de Python qui sont installés si vous activez la fonctionnalité **Machine Learning Services (de-de base de données)** et sélectionnez les Python comme la langue.

> [!NOTE]
> Prise en charge de Python est une fonctionnalité en version préliminaire et est toujours en cours de développement.

## <a name="python-components"></a>Composants de Python

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ne modifiez pas les exécutables de Python. Le runtime Python est installé indépendamment des outils SQL et est exécuté en dehors de la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] processus.

La distribution est associée à un spécifique [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instance se trouve dans le dossier associé à l’instance.

Par exemple, si vous avez installé les Services de Machine Learning avec l’option de Python sur l’instance par défaut, regardez sous :

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER`

Installation de SQL Server 2017 Machine Learning Services ajoute la distribution Anaconda de Python. Plus précisément, les programmes d’installation Anaconda 3 sont utilisés, en fonction de la branche Anaconda 4.3. Niveau de SQL Server 2017 Python attendu est Python 3.5.

## <a name="new-in-this-release"></a>Nouveautés dans cette version

Pour obtenir la liste des packages pris en charge par la distribution Anaconda, consultez le site d’analytique Continuum : [liste des packages Anaconda](https://docs.continuum.io/anaconda/pkg-docs)

Machine Learning Services dans SQL Server 2017 inclut également la nouvelle **revoscalepy** bibliothèque pour Python.

Cette bibliothèque fournit des fonctionnalités équivalentes à celles de la **RevoScaleR** package pour Microsoft R. En d’autres termes, il prend en charge la création de contextes de calcul à distance, ainsi que divers modèles d’apprentissage de machines évolutive, tel que **rxLinMod**. Pour plus d’informations sur RevoScaleR, consultez [distribué et le calcul parallèle avec ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing).

Étant donné que prennent en charge pour Python est une fonctionnalité en version préliminaire et toujours en cours de développement, le **revoscalepy** actuellement, bibliothèque inclut uniquement un sous-ensemble des fonctionnalités RevoScaleR. 

Les ajouts peuvent inclure la [Microsoft cognitifs Toolkit](https://www.microsoft.com/research/product/cognitive-toolkit/). Anciennement appelé CNTK, cette bibliothèque prend en charge une variété de modèles de réseau neuronal, y compris à convolution réseaux (CNN), réseaux ponctuelle (RNN) et Long mémoire court de terme (LSTM).

## <a name="using-python-in-sql-server"></a>À l’aide de Python dans SQL Server

Vous importez le **revoscalepy** module dans votre code Python et appeler des fonctions à partir du module, comme d’autres fonctions de Python.

Les données d’entrée pour Python doivent être sous forme de tableau. Tous les résultats de Python doivent être retournés sous la forme d’un **pandas** trame de données.

Vous pouvez exécuter votre code Python à l’intérieur de T-SQL, en incorporant le script dans une procédure stockée.

Ou, exécutez le code à partir d’un IDE Python local et que le script exécuté sur l’ordinateur SQL Server, en définissant un contexte de calcul à distance.

Vous pouvez utiliser des données locales, obtenir des données à partir de SQL Server ou d’autres sources de données ODBC ou utiliser le format de fichier XDF pour échanger des données avec d’autres sources, ou avec des solutions R.

**Pour plus d’informations**

+ Fonctions prises en charge : [What ' s revoscalepy](what-is-revoscalepy.md) 
+ Prise en charge des types de données Python : [Python bibliothèques et Types de données](python-libraries-and-data-types.md)
+ Prise en charge des sources de données : ODBC bases de données, SQL Server et les fichiers XDF
+ Prise en charge des contextes de calcul : local ou SQL Server

### <a name="licensing"></a>Gestionnaire de licences

Dans le cadre de l’installation des Services d’apprentissage Machine avec Python, vous devez accepter les termes du contrat de la licence publique GNU.

## <a name="see-also"></a>Voir aussi

[Les Types de données et les bibliothèques de Python](python-libraries-and-data-types.md)

