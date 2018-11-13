# PHP PDO Ussage

## Database Connection
    try {
        $db = new PDO("mysql:host=localhost;dbname=DB_NAME;charset=utf8", "root", "PASSWORD");
    } catch (PDOException $e) {
        echo $e->getMessage();
    }
    
## Multiple Select
    $query = $db->query("SELECT * FROM TABLE_NAME", PDO::FETCH_OBJ);
    if ($query->rowCount()) {
        foreach ($query as $row) {
            print_r($row);
        }
    } else {
        echo 'ERROR';
    }
    
## Single Select
    $query = $db->query("SELECT * FROM TABLE_NAME")->fetch(PDO::FETCH_OBJ);
    if ($query) {
        print_r($query);
    } else {
        echo 'ERROR';
    }

## Insert
    $query = $db->prepare("INSERT INTO TABLE_NAME SET COLUMN_NAME = ?, COLUMN_NAME = ?");
    $insert = $query->execute(array("DATA", "DATA"));
    if ($insert) {
        echo 'OK';
    } else {
        echo 'ERROR';
    }

## Update 
    $query = $db->prepare("UPDATE TABLE_NAME SET COLUMN_NAME = ?, COLUMN_NAME = ? WHERE id = 1");
    $update = $query->execute(array("DATA", "DATA"));
    if ($update) {
        echo 'OK';
    } else {
        echo 'ERROR';
    }

## Multiple Delete
    $delete = $db->exec("DELETE FROM TABLE_NAME");
    if ($delete) {
        echo $delete;
    } else {
        echo 'ERROR';
    }
    
## Single Delete
    $query = $db->prepare("DELETE FROM TABLE_NAME WHERE id = ?");
    $delete = $query->execute(array("DATA"));
    if ($delete) {
        echo 'OK';
    } else {
        echo 'ERROR';
    }
    
 ## Close Database Connection
    $db = null;
