---
title: Exemple de mise à jour de données volumineuses | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 231125f60ec0c5791e55a10cff56b3b93339fb91
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027074"
---
# <a name="updating-large-data-sample"></a>Exemple de mise à jour de données volumineuses

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] montre comment mettre à jour une grande colonne dans une base de données.

Le fichier de code pour cet exemple se nomme UpdateLargeData.java et se trouve à l’emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d’application, l’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est nécessaire. Vous devez également définir l'instruction classpath de façon à inclure le fichier sqljdbc4.jar. Si l'instruction classpath n'a pas d'entrée pour sqljdbc4.jar, l'exemple d'application lève l'exception usuelle « Classe introuvable ». Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit les fichiers de bibliothèques de classes sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar ou sqljdbc42.jar, à utiliser en fonction de vos paramètres JRE (Java Runtime Environment). Cet exemple utilise les méthodes [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) et [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md), qui sont introduites dans l’API JDBC 4.0, pour accéder aux méthodes de mise en mémoire tampon des réponses spécifiques aux pilotes. Pour pouvoir compiler et exécuter cet exemple, vous devez disposer de la bibliothèque de classes sqljdbc4.jar, qui assure la prise en charge de JDBC 4.0. Pour plus d’informations sur le fichier JAR à choisir, voir [Configuration requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Exemple

Dans l’exemple suivant, le code établit une connexion à la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. L’exemple de code crée ensuite un objet Statement et utilise la méthode [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) pour vérifier si l’objet Statement est un wrapper pour la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) spécifiée. La méthode [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) permet d’accéder aux méthodes de mise en mémoire tampon des réponses spécifiques aux pilotes.

L’exemple de code définit ensuite le mode de mise en mémoire tampon des réponses comme étant **adaptatif** avec la méthode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) ; il montre également comment obtenir le mode de mise en mémoire tampon adaptatif.

Il exécute ensuite l’instruction SQL et place les données retournées dans un objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) pouvant être mis à jour.

Pour finir, l’exemple de code boucle dans les lignes de données du jeu de résultats. S’il trouve un résumé de document vide, il utilise la combinaison des méthodes [updateString](../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) et [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) pour mettre à jour la ligne de données et la réenregistrer dans la base de données. Si des données sont déjà présentes, l’exemple utilise la méthode [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) pour afficher une partie des données.

Le comportement par défaut du pilote est « **adaptatif** ». Cependant, pour les jeux de résultats pouvant être mis à jour vers l’avant uniquement et quand la taille des données du jeu de résultats est supérieure à la capacité mémoire de l’application, cette dernière doit définir explicitement le mode de mise en mémoire tampon adaptatif avec la méthode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md).

[!code[JDBC#UsingAdaptiveBuffering3](../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]

## <a name="see-also"></a>Voir aussi

[Utilisation de données volumineuses](../../connect/jdbc/working-with-large-data.md)
