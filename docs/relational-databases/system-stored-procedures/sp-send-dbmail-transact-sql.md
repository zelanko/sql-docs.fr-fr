---
title: sp_send_dbmail (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sendmail_sp_TSQL
- sendmail_sp
- SP_SEND_DBMAIL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_send_dbmail
ms.assetid: f1d7a795-a3fd-4043-ac4b-c781e76dab47
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52a89c0220bddde6944e759936dc22ad1f3e0ff2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126302"
---
# <a name="spsenddbmail-transact-sql"></a>sp_send_dbmail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Envoie un message électronique aux destinataires spécifiés. Le message peut comprendre un ensemble de résultats de requête et des fichiers joints. Lors de la messagerie est correctement placée dans la file d’attente de la messagerie de base de données, **sp_send_dbmail** retourne le **mailitem_id** du message. Cette procédure stockée se trouve dans le **msdb** base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_send_dbmail [ [ @profile_name = ] 'profile_name' ]  
    [ , [ @recipients = ] 'recipients [ ; ...n ]' ]  
    [ , [ @copy_recipients = ] 'copy_recipient [ ; ...n ]' ]  
    [ , [ @blind_copy_recipients = ] 'blind_copy_recipient [ ; ...n ]' ]  
    [ , [ @from_address = ] 'from_address' ]  
    [ , [ @reply_to = ] 'reply_to' ]   
    [ , [ @subject = ] 'subject' ]   
    [ , [ @body = ] 'body' ]   
    [ , [ @body_format = ] 'body_format' ]  
    [ , [ @importance = ] 'importance' ]  
    [ , [ @sensitivity = ] 'sensitivity' ]  
    [ , [ @file_attachments = ] 'attachment [ ; ...n ]' ]  
    [ , [ @query = ] 'query' ]  
    [ , [ @execute_query_database = ] 'execute_query_database' ]  
    [ , [ @attach_query_result_as_file = ] attach_query_result_as_file ]  
    [ , [ @query_attachment_filename = ] query_attachment_filename ]  
    [ , [ @query_result_header = ] query_result_header ]  
    [ , [ @query_result_width = ] query_result_width ]  
    [ , [ @query_result_separator = ] 'query_result_separator' ]  
    [ , [ @exclude_query_output = ] exclude_query_output ]  
    [ , [ @append_query_error = ] append_query_error ]  
    [ , [ @query_no_truncate = ] query_no_truncate ]   
    [ , [ @query_result_no_padding = ] @query_result_no_padding ]   
    [ , [ @mailitem_id = ] mailitem_id ] [ OUTPUT ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_name = ] 'profile_name'` Est le nom du profil à envoyer le message à partir de. Le *profile_name* est de type **sysname**, avec NULL comme valeur par défaut. Le *profile_name* doit être le nom d’un profil de messagerie de base de données existant. En cas de non *profile_name* est spécifié, **sp_send_dbmail** utilise le profil privé par défaut pour l’utilisateur actuel. Si l’utilisateur ne dispose pas d’un profil privé par défaut, **sp_send_dbmail** utilise le profil public par défaut pour le **msdb** base de données. Si l’utilisateur ne dispose pas d’un profil privé par défaut et il n’existe aucun profil public par défaut pour la base de données, **@profile_name** doit être spécifié.  
  
`[ @recipients = ] 'recipients'` Est une liste délimitée par des points-virgules d’adresses de messagerie à laquelle envoyer le message. La liste de destinataires est de type **varchar (max)** . Bien que ce paramètre est facultatif, au moins une des **@recipients** , **@copy_recipients** , ou **@blind_copy_recipients** doit être spécifié, ou **sp_ send_dbmail** renvoie une erreur.  
  
`[ @copy_recipients = ] 'copy_recipients'` Est qu'une liste délimitée par des points-virgules de courrier électronique adresses en copie carbone du message. La liste de destinataires de copie est de type **varchar (max)** . Bien que ce paramètre est facultatif, au moins une des **@recipients** , **@copy_recipients** , ou **@blind_copy_recipients** doit être spécifié, ou **sp_ send_dbmail** renvoie une erreur.  
  
`[ @blind_copy_recipients = ] 'blind_copy_recipients'` Est qu'une liste délimitée par des points-virgules de courrier électronique adresses en copie conforme invisible du message. La liste de destinataires de copie invisible est de type **varchar (max)** . Bien que ce paramètre est facultatif, au moins une des **@recipients** , **@copy_recipients** , ou **@blind_copy_recipients** doit être spécifié, ou **sp_ send_dbmail** renvoie une erreur.  
  
`[ @from_address = ] 'from_address'` Est la valeur de l’adresse' du message électronique de'. Il s'agit d'un paramètre optionnel utilisé pour remplacer les paramètres dans le profil de messagerie. Ce paramètre est de type **varchar (max)** . Les paramètres de sécurité SMTP déterminent si ces substitutions sont acceptées. Si aucun paramètre n'est spécifié, la valeur par défaut est NULL.  
  
`[ @reply_to = ] 'reply_to'` Est la valeur de « adresse de réponse » du message électronique. Une seule adresse de messagerie est acceptée comme valeur valide. Il s'agit d'un paramètre optionnel utilisé pour remplacer les paramètres dans le profil de messagerie. Ce paramètre est de type **varchar (max)** . Les paramètres de sécurité SMTP déterminent si ces substitutions sont acceptées. Si aucun paramètre n'est spécifié, la valeur par défaut est NULL.  
  
`[ @subject = ] 'subject'` Fait l’objet du message électronique. L’objet est de type **nvarchar (255)** . Si l'objet est omis, « Message SQL Server » est la valeur par défaut.  
  
`[ @body = ] 'body'` Est le corps du message électronique. Le corps du message est de type **nvarchar (max)** , avec NULL comme valeur par défaut.  
  
`[ @body_format = ] 'body_format'` Est le format du corps du message. Le paramètre est de type **varchar (20)** , avec NULL comme valeur par défaut. Lorsqu'il est spécifié, les en-têtes du message sortant sont définis pour indiquer le format choisi pour le corps de message. Il peut contenir l'une des valeurs suivantes :  
  
-   TEXT  
  
-   HTML  
  
 La valeur par défaut est TEXT.  
  
`[ @importance = ] 'importance'` Est l’importance du message. Le paramètre est de type **varchar(6)** . Il peut contenir l'une des valeurs suivantes :  
  
-   Faible  
  
-   Normale  
  
-   Élevé  
  
 La valeur par défaut est Normal.  
  
`[ @sensitivity = ] 'sensitivity'` Est la sensibilité du message. Le paramètre est de type **varchar(12)** . Il peut contenir l'une des valeurs suivantes :  
  
-   Normale  
  
-   Personal  
  
-   Privé  
  
-   Confidential  
  
 La valeur par défaut est Normal.  
  
`[ @file_attachments = ] 'file_attachments'` Est une liste délimitée par des points-virgules des noms de fichiers à joindre au message électronique. Les fichiers de la liste doivent être spécifiés sous forme de chemins d'accès absolus. La liste des pièces jointes est de type **nvarchar (max)** . Par défaut, la messagerie de base de données limite la taille des pièces jointes à 1 Mo par fichier.  
  
`[ @query = ] 'query'` Est une requête à exécuter. Les résultats de la requête sont inclus dans le corps du message électronique ou attachés comme pièce jointe. La requête est de type **nvarchar (max)** et peut contenir toute valide [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions. Notez que la requête est exécutée dans une session distincte, : les variables locales du script appelant **sp_send_dbmail** ne sont pas disponibles à la requête.  
  
`[ @execute_query_database = ] 'execute_query_database'` Est le contexte de base de données dans laquelle la procédure stockée s’exécute la requête. Le paramètre est de type **sysname**, avec une valeur par défaut de la base de données actuelle. Ce paramètre s’applique uniquement si **@query** est spécifié.  
  
`[ @attach_query_result_as_file = ] attach_query_result_as_file` Indique si le jeu de résultats de la requête est retourné comme pièce jointe. *attach_query_result_as_file* est de type **bits**, avec 0 comme valeur par défaut.  
  
 Lorsque la valeur est 0, les résultats de requête sont inclus dans le corps du message électronique, après le contenu de la **@body** paramètre. Lorsque la valeur est 1, les résultats sont retournés comme pièce jointe. Ce paramètre s’applique uniquement si **@query** est spécifié.  
  
`[ @query_attachment_filename = ] query_attachment_filename` Spécifie le nom de fichier à utiliser pour le jeu de résultats de la pièce jointe de requête. *query_attachment_filename* est de type **nvarchar (255)** , avec NULL comme valeur par défaut. Ce paramètre est ignoré lorsque *attach_query_result* est 0. Lorsque *attach_query_result* est 1, et ce paramètre est NULL, la messagerie de base de données crée un nom de fichier arbitraire.  
  
`[ @query_result_header = ] query_result_header` Spécifie si les résultats de la requête incluent les en-têtes de colonne. La valeur de query_result_header est de type **bits**. Lorsque la valeur est 1, les résultats de la requête contiennent des en-têtes de colonne, et lorsque la valeur est 0, les résultats n'incluent aucun en-tête de colonne. Ce paramètre par défaut est **1**. Ce paramètre s’applique uniquement si **@query** est spécifié.  
 
   >[!NOTE]
   > L’erreur suivante peut se produire lors de la définition @query_result_header à 0 et en affectant @query_no_truncate à 1 :
   > <br> Msg 22050, niveau 16, état 1, ligne 12 : Impossible d’initialiser la bibliothèque sqlcmd avec le numéro d’erreur-2147024809.
  
`[ @query_result_width = ] query_result_width` Est la largeur de ligne, en caractères, à utiliser pour mettre en forme les résultats de la requête. Le *query_result_width* est de type **int**, avec une valeur par défaut de 256. La valeur fournie doit être comprise entre 10 et 32767. Ce paramètre s’applique uniquement si **@query** est spécifié.  
  
`[ @query_result_separator = ] 'query_result_separator'` Le caractère est utilisé pour séparer les colonnes dans la sortie de requête. Le séparateur est de type **char (1)** . La valeur par défaut est ' ' (espace).  
  
`[ @exclude_query_output = ] exclude_query_output` Spécifie s’il faut retourner la sortie de l’exécution des requêtes dans le message électronique. **exclude_query_output** est de type bit, avec 0 comme valeur par défaut. Lorsque ce paramètre est 0, l’exécution de la **sp_send_dbmail** procédure stockée imprime le message retourné comme résultat de l’exécution des requêtes sur la console. Lorsque ce paramètre est 1, l’exécution de la **sp_send_dbmail** procédure stockée n’imprime aucun des messages de l’exécution de requête sur la console.  
  
`[ @append_query_error = ] append_query_error` Spécifie s’il faut envoyer le message électronique lorsqu’une erreur est retournée à partir de la requête spécifiée dans le **@query** argument. **append_query_error** est **bits**, avec 0 comme valeur par défaut. Lorsque la valeur de ce paramètre est 1, la messagerie de base de données envoie le message électronique et inclut le message d'erreur de la requête dans le corps du message. Lorsque ce paramètre est 0, la messagerie de base de données n’envoie pas de message électronique, et **sp_send_dbmail** se termine par le code de retour 1, indiquant un échec.  
  
`[ @query_no_truncate = ] query_no_truncate` Spécifie s’il faut exécuter la requête avec l’option qui permet d’éviter la troncation des types de données de longueur variable (**varchar (max)** , **nvarchar (max)** , **varbinary (max)** **xml**, **texte**, **ntext**, **image**et les types de données définis par l’utilisateur). Lorsqu'ils sont définis, les résultats de requête n'incluent pas les en-têtes de colonne. Le *query_no_truncate* valeur est de type **bits**. Lorsque la valeur est définie à 0 ou lorsqu'elle n'est pas spécifiée, les colonnes de la requête sont limitées à 256 caractères, si elle est définie à 1, les colonnes ne sont pas tronquées. La valeur par défaut de ce paramètre est 0.  
  
> [!NOTE]  
>  Lorsqu’il est utilisé avec grandes quantités de données, le @**query_no_truncate** option consomme des ressources supplémentaires et peut ralentir les performances du serveur.  
  
`[ @query_result_no_padding ] @query_result_no_padding` Le type est bit. La valeur par défaut est 0. Lorsque vous définissez sur 1, les résultats de requête ne sont pas complétées, ce qui peut réduire la taille du fichier. Si vous définissez @query_result_no_padding à 1 et que vous définissez le @query_result_width paramètre, le @query_result_no_padding paramètre remplace le @query_result_width paramètre.  
  
 Dans ce cas, aucune erreur ne se produit.  
 
  >[!NOTE]
  > L’erreur suivante peut se produire lors de la définition @query_result_no_padding à 1 et en fournissant un paramètre pour @query_no_truncate:
  > <br> Msg 22050, niveau 16, état 1, ligne 0 : Impossible d’exécuter la requête, car le @query_result_no_append et @query_no_truncate options s’excluent mutuellement. 
  
 Si vous définissez la @query_result_no_padding à 1 et que vous définissez le @query_no_truncate paramètre, une erreur est générée.  
  
`[ @mailitem_id = ] mailitem_id [ OUTPUT ]` Paramètre de sortie facultatif retourne la *mailitem_id* du message. Le *mailitem_id* est de type **int**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Un code de retour de 0 indique le succès. Une autre valeur signifie l'échec. Le code d’erreur pour l’instruction qui a échoué est stocké dans le @@ERROR variable.  
  
## <a name="result-sets"></a>Jeux de résultats  
 En cas de succès, le message « Courrier en file d'attente » est renvoyé.  
  
## <a name="remarks"></a>Notes  
 Avant de l’utiliser, la messagerie de base de données doit être activé à l’aide de l’Assistant Configuration de la messagerie de base de données, ou **sp_configure**.  
  
 **sysmail_stop_sp** arrête la messagerie de base de données en arrêtant les objets Service Broker qui utilise le programme externe. **sp_send_dbmail** accepte toujours les messages lors de la messagerie de base de données est arrêtée à l’aide de **sysmail_stop_sp**. Pour démarrer la messagerie de base de données, utilisez **sysmail_start_sp**.  
  
 Lorsque **@profile** n’est pas spécifié, **sp_send_dbmail** utilise un profil par défaut. Si l'utilisateur expéditeur du message électronique a un profil privé par défaut, la messagerie de base de données utilise ce profil. Si l’utilisateur ne dispose d’aucun profil privé par défaut, **sp_send_dbmail** utilise le profil public par défaut. S’il n’existe aucun profil privé par défaut pour l’utilisateur et aucun profil public par défaut, **sp_send_dbmail** retourne une erreur.  
  
 **sp_send_dbmail** ne prend pas en charge les messages électroniques sans contenu. Pour envoyer un message électronique, vous devez spécifier au moins une des **@body** , **@query** , **@file_attachments** , ou **@subject** . Sinon, **sp_send_dbmail** retourne une erreur.  
  
 La messagerie de base de données utilise le contexte de sécurité [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows de l'utilisateur actuel pour contrôler l'accès aux fichiers. Par conséquent, les utilisateurs sont authentifiés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification ne peut pas joindre des fichiers à l’aide de **@file_attachments** . Windows n'autorise pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à fournir des informations d'identification d'un ordinateur distant à un autre. De cette façon, la messagerie de base de données ne peut pas joindre de fichiers aux messages depuis un partage réseau lorsque la commande est exécutée par un ordinateur autre que celui sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute.  
  
 Si les deux **@query** et **@file_attachments** sont spécifiés et ne peut pas trouver le fichier, la requête est toujours exécutée, mais le message électronique n’est pas envoyé.  
  
 Lorsqu'une requête est spécifiée, l'ensemble de résultats se présente sous la forme d'un texte inséré. Les données binaires contenues dans le résultat sont envoyées au format hexadécimal.  
  
 Les paramètres **@recipients** , **@copy_recipients** , et **@blind_copy_recipients** sont séparés par des points-virgules des listes d’adresses de messagerie. Au moins un de ces paramètres doit être fourni, ou **sp_send_dbmail** retourne une erreur.  
  
 Lors de l’exécution **sp_send_dbmail** sans un contexte de transaction, la messagerie de base de données démarre et valide une transaction implicite. Lors de l’exécution **sp_send_dbmail** à partir d’une transaction existante, messagerie de base de données s’appuie sur l’utilisateur pour valider ou annuler les modifications. Aucune transaction interne n'est lancée.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution **sp_send_dbmail** par défaut à tous les membres de la **DatabaseMailUser** rôle de base de données dans le **msdb** base de données. Toutefois, lorsque l’utilisateur expéditeur du message n’a pas l’autorisation d’utiliser le profil pour la demande, **sp_send_dbmail** retourne une erreur et n’envoie pas le message.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-sending-an-e-mail-message"></a>R. Envoi d'un message électronique  
 Cet exemple envoie un message électronique à votre ami à l’aide de l’adresse de messagerie `myfriend@Adventure-Works.com`. Le message a comme objet `Automated Success Message`. Le corps du message contient la phrase `'The stored procedure finished successfully'`.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>B. Envoi d'un message électronique avec les résultats d'une requête  
 Cet exemple envoie un message électronique à votre ami à l’aide de l’adresse de messagerie `yourfriend@Adventure-Works.com`. Le message a comme objet `Work Order Count` et exécute une requête qui affiche le nombre d'ordres de travail pour lesquels une date `DueDate` ne dépasse pas le 30 avril 2004 de plus de deux jours. La messagerie de base de données joint le résultat au courrier sous la forme d'un fichier texte.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @query = 'SELECT COUNT(*) FROM AdventureWorks2012.Production.WorkOrder  
                  WHERE DueDate > ''2004-04-30''  
                  AND  DATEDIFF(dd, ''2004-04-30'', DueDate) < 2' ,  
    @subject = 'Work Order Count',  
    @attach_query_result_as_file = 1 ;  
```  
  
### <a name="c-sending-an-html-e-mail-message"></a>C. Envoi d'un message électronique au format HTML  
 Cet exemple envoie un message électronique à votre ami à l’aide de l’adresse de messagerie `yourfriend@Adventure-Works.com`. Le message a comme objet `Work Order List` et affiche un document HTML montrant les ordres de travail pour lesquels la valeur de `DueDate` ne dépasse pas le 30 avril 2004 de plus de deux jours. La messagerie de base de données envoie le message au format HTML.  
  
```  
DECLARE @tableHTML  NVARCHAR(MAX) ;  
  
SET @tableHTML =  
    N'<H1>Work Order Report</H1>' +  
    N'<table border="1">' +  
    N'<tr><th>Work Order ID</th><th>Product ID</th>' +  
    N'<th>Name</th><th>Order Qty</th><th>Due Date</th>' +  
    N'<th>Expected Revenue</th></tr>' +  
    CAST ( ( SELECT td = wo.WorkOrderID,       '',  
                    td = p.ProductID, '',  
                    td = p.Name, '',  
                    td = wo.OrderQty, '',  
                    td = wo.DueDate, '',  
                    td = (p.ListPrice - p.StandardCost) * wo.OrderQty  
              FROM AdventureWorks.Production.WorkOrder as wo  
              JOIN AdventureWorks.Production.Product AS p  
              ON wo.ProductID = p.ProductID  
              WHERE DueDate > '2004-04-30'  
                AND DATEDIFF(dd, '2004-04-30', DueDate) < 2   
              ORDER BY DueDate ASC,  
                       (p.ListPrice - p.StandardCost) * wo.OrderQty DESC  
              FOR XML PATH('tr'), TYPE   
    ) AS NVARCHAR(MAX) ) +  
    N'</table>' ;  
  
EXEC msdb.dbo.sp_send_dbmail @recipients='yourfriend@Adventure-Works.com',  
    @subject = 'Work Order List',  
    @body = @tableHTML,  
    @body_format = 'HTML' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Objets de Configuration de messagerie de base de données](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
