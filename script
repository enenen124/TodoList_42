document.addEventListener('DOMContentLoaded', () => {
    const todoForm = document.getElementById('todo-form');
    const todoInput = document.getElementById('todo-input');
    const todoList = document.getElementById('todo-list');

    // 从本地存储加载任务
    let todos = JSON.parse(localStorage.getItem('todos')) || [];

    // 渲染任务列表
    function renderTodos() {
        todoList.innerHTML = '';
        todos.forEach((todo, index) => {
            const li = document.createElement('li');
            li.className = `todo-item ${todo.completed ? 'completed' : ''}`;
            li.innerHTML = `
                <input type="checkbox" ${todo.completed ? 'checked' : ''} onchange="toggleTodo(${index})">
                <span>${todo.text}</span>
                <button class="delete-btn" onclick="deleteTodo(${index})">删除</button>
            `;
            todoList.appendChild(li);
        });
    }

    // 添加新任务
    todoForm.addEventListener('submit', (e) => {
        e.preventDefault();
        const text = todoInput.value.trim();
        if (text) {
            todos.push({ text, completed: false });
            saveTodos();
            renderTodos();
            todoInput.value = '';
        }
    });

    // 切换任务完成状态
    window.toggleTodo = (index) => {
        todos[index].completed = !todos[index].completed;
        saveTodos();
        renderTodos();
    };

    // 删除任务
    window.deleteTodo = (index) => {
        todos.splice(index, 1);
        saveTodos();
        renderTodos();
    };

    // 保存任务到本地存储
    function saveTodos() {
        localStorage.setItem('todos', JSON.stringify(todos));
    }

    // 初始渲染
    renderTodos();
});
