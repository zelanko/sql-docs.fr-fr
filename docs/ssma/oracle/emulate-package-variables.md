---
title: Émulation de variables de package Oracle
description: Décrit comment Assistant Migration SQL Server (SSMA) pour Oracle émule les variables de package Oracle dans SQL Server.
authors: nahk-ivanov
ms.service: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: 9a8ca5c7dfdda98e1c005c3851d061957cf67449
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "76762823"
---
# <a name="emulating-oracle-package-variables"></a>Émulation de variables de package Oracle

Oracle prend en charge l’encapsulation des variables, des types, des procédures stockées et des fonctions dans un package. Lorsque vous convertissez des packages Oracle, vous devez convertir :

* Procédures et fonctions-public et privé
* Variables
* Curseurs
* Routines d’initialisation

Cet article explique comment Assistant Migration SQL Server (SSMA) pour Oracle convertit les variables de package en SQL Server.

## <a name="conversion-basics"></a>Notions de base de la conversion

Pour stocker les variables de package, SSMA pour Oracle utilise des procédures stockées qui résident dans `ssma_oracle` un schéma spécial `ssma_oracle.db_storage` et une table. Cette table est filtrée par `SPID` (identificateur de session) et par heure de connexion. Ce filtrage vous permet de faire la distinction entre les variables de différentes sessions.

Au début de chaque procédure de package convertie, SSMA passe un `ssma_oracle.db_check_init_package` appel à la procédure spéciale, qui vérifie si le package est initialisé et l’initialise si nécessaire. Chaque procédure d’initialisation nettoie la table de stockage et définit les valeurs par défaut pour chaque variable de package.

## <a name="example"></a>Exemple

Prenons l’exemple suivant pour la conversion de plusieurs variables de package :

```sql
CREATE OR REPLACE PACKAGE MY_PACKAGE
IS
    space varchar(1) := ' ';
    unitname varchar(128) := 'My Simple Package';
    ts date := sysdate;
END;
```

SSMA le convertit en code Transact-SQL suivant :

```sql
CREATE PROCEDURE dbo.MY_PACKAGE$SSMA_Initialize_Package
AS
BEGIN
    EXECUTE ssma_oracle.db_clean_storage

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'SPACE',
        ' '

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'UNITNAME',
        'My Simple Package'

    DECLARE
        @temp datetime2

    SET @temp = sysdatetime()

    EXECUTE sysdb.ssma_oracle.set_pv_datetime2
      DB_NAME(),
      'DBO',
      'MY_PACKAGE',
      'TS',
      @temp
END
```

## <a name="emulating-get-and-set-methods-for-package-variables"></a>Émulation des méthodes d’extraction et de définition pour les variables de package

Oracle utilise `Get` et `Set` des méthodes pour les variables de package, afin d’éviter de laisser d’autres sous-programmes lire et les écrire directement. S’il est nécessaire de conserver certaines variables disponibles entre les appels de sous-programme au cours de la même session, ces variables sont traitées comme des variables globales.

Pour surmonter cette règle de portée, SSMA pour Oracle utilise des procédures `ssma_oracle.set_pv_varchar` stockées comme pour chaque type de variable. Pour accéder à ces variables, SSMA utilise un ensemble de `get_*` `set_*` procédures et de fonctions indépendantes de la transaction.

| Type de données dans Oracle | Procédure `Set` SSMA           |
| ------------------- | ------------------------------ |
| VARCHAR             | `ssma_oracle.set_pv_varchar`   |
| DATE                | `ssma_oracle.set_pv_datetime2` |
| CHAR                | `ssma_oracle.set_pv_varchar`   |
| INT                 | `ssma_oracle.set_pv_float`     |
| FLOAT               | `ssma_oracle.set_pv_float`     |

Pour faire la distinction entre les variables de différentes sessions, SSMA stocke les `SPID` variables ainsi que leur (identificateur de session) et l’heure de connexion de la session. Ainsi, `get_*` les `set_*` procédures et maintiennent les variables indépendamment des sessions qui les exécutent.
