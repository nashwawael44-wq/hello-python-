# hello-python-
# ===== مدير المهام =====

# حفظ المهام في ملف
def save_tasks(tasks):
    with open("tasks.txt", "w", encoding="utf-8") as file:
        for task in tasks:
            file.write(task + "\n")


# تحميل المهام من الملف
def load_tasks():
    try:
        with open("tasks.txt", "r", encoding="utf-8") as file:
            return [line.strip() for line in file.readlines()]
    except FileNotFoundError:
        return []


# تحميل المهام القديمة
tasks = load_tasks()


# تشغيل البرنامج
while True:

    print("\n--- مدير المهام المطور ---")
    print("1. إضافة مهمة")
    print("2. عرض المهام")
    print("3. حذف مهمة محددة")
    print("4. خروج")

    choice = input("اختاري رقم العملية: ")

    # إضافة مهمة
    if choice == '1':

        task = input("اكتبي المهمة الجديدة: ")
        tasks.append(task)

        save_tasks(tasks)

        print("✅ تمت الإضافة")

    # عرض المهام
    elif choice == '2':

        if len(tasks) == 0:
            print("📭 لا توجد مهام")

        else:
            print("\n📋 مهامك الحالية:")

            for i, t in enumerate(tasks):
                print(f"{i+1}. {t}")

    # حذف مهمة
    elif choice == '3':

        if len(tasks) == 0:

            print("❌ مفيش مهام عشان تمسحيها")

        else:

            print("\n📋 المهام:")

            for i, t in enumerate(tasks):
                print(f"{i+1}. {t}")

            num = int(input("اكتبي رقم المهمة اللي عايزة تمسحيها: "))

            if 0 < num <= len(tasks):

                removed = tasks.pop(num - 1)

                save_tasks(tasks)

                print(f"🗑️ تم حذف: {removed}")

            else:
                print("⚠️ رقم غلط")

    # خروج
    elif choice == '4':

        print("👋 مع السلامة")

        break

    else:
        print("❌ اختيار غير صحيح")
