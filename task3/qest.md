## Этап 3: Рефакторинг и код-ревью (30 минут)

### Задачи
1. Оценить предложенный код.
2. Предложить улучшения.
3. Провести рефакторинг.
4. Объяснить, почему изменения делают код лучше (удобнее для сопровождения, производительнее и т.д.).

### Код для анализа и рефакторинга

```javascript
function processTasks(tasks) {
    let completedTasks = [];
    let pendingTasks = [];
    let overdueTasks = [];
    
    for (let i = 0; i < tasks.length; i++) {
        let task = tasks[i];
        if (task.status === 'completed') {
            if (!task.dateCompleted) {
                task.dateCompleted = new Date();
            }
            completedTasks.push(task);
            console.log('Task ' + task.name + ' is completed');
        } else if (task.status === 'pending') {
            if (task.dueDate && new Date(task.dueDate) < new Date()) {
                overdueTasks.push(task);
                console.log('Task ' + task.name + ' is overdue');
            } else {
                pendingTasks.push(task);
                console.log('Task ' + task.name + ' is pending');
            }
        } else if (task.status === 'canceled') {
            console.log('Task ' + task.name + ' is canceled');
        } else {
            console.log('Unknown status for task ' + task.name);
        }
    }

    return {
        completed: completedTasks,
        pending: pendingTasks,
        overdue: overdueTasks,
    };
}
```

#### Подзадачи для этапа 3:
1. Провести анализ кода: читаемость, повторяемость, обработка ошибок, side effects.
2. Предложить улучшения (например, вынести логику в отдельные функции, убрать лишние side effects, использовать современные методы массива).
3. Провести рефакторинг кода.
4. Объяснить, почему предложенные изменения улучшают код.

---