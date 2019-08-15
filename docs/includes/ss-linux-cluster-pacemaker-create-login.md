---
ms.openlocfilehash: d2519b1cc56081f8a35308ac41e11f46a7f97211
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215603"
---
1. **Sur tous les serveurs SQL Server, créez un compte de connexion Server pour Pacemaker**. Le code Transact-SQL ci-dessous a pour effet de créer un compte de connexion :

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

  Au moment de la création du groupe de disponibilité, l’utilisateur Pacemaker requiert des autorisations ALTER, CONTROL et VIEW DEFINITION sur le groupe de disponibilité, une fois qu’il a été créé mais avant l’ajout de nœuds à celui-ci.

1. **Sur tous les serveurs SQL Server, enregistrez les informations d’identification pour le compte de connexion SQL Server**.

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
