<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task Tracker</title>
</head>
<body>
    <h1>Task Tracker</h1>

    <ul id="taskList">
        <!-- タスクが表示される場所 -->
    </ul>

    <input type="text" id="taskInput" placeholder="新しいタスクを追加">
    <button onclick="addTask()">追加</button>

    <script src="app.js"></script>
</body>
</html>
// タスク一覧
const tasks = [];

// タスクを表示する関数
function displayTasks() {
    const taskList = document.getElementById('taskList');
    taskList.innerHTML = ''; // タスクリストをクリア

    tasks.forEach((task, index) => {
        const li = document.createElement('li');
        li.textContent = task;
        li.onclick = () => completeTask(index); // クリックでタスク完了
        taskList.appendChild(li);
    });
}

// タスクを追加する関数
function addTask() {
    const taskInput = document.getElementById('taskInput');
    const newTask = taskInput.value;

    if (newTask.trim() !== '') {
        tasks.push(newTask);
        taskInput.value = ''; // 入力フィールドをクリア
        displayTasks();
    }
}

// タスクを完了させる関数
function completeTask(index) {
    tasks.splice(index, 1); // タスクを削除
    displayTasks();
}

// 最初にタスクを表示
displayTasks();
