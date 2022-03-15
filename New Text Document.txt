the Course class
 public void printCourceStudents() {
        Enumeration en = courseRecords.elements();
        System.out.println("Course has "+ courseRecords.size() + " Students");
        while (en.hasMoreElements()) {
            CourseRecord cr = (CourseRecord) en.nextElement();
            System.out.println(cr.getStudent().getName());
        }
    }
 public void printBestStudent() throws NotYetSetException {
        double best_average = 0.0;
        String student_name = null ;
        Enumeration en = courseRecords.elements();
        while (en.hasMoreElements()) {
            CourseRecord cr = (CourseRecord) en.nextElement();
            if (best_average < cr.average()) {
                best_average = cr.average();
                student_name = cr.getStudent().getName();
            }
        }
        System.out.println("Best Student is " + student_name);

    }

 public void printFinalExamStudents() throws NotYetSetException {
        double best_average = 0.0;
        double average = 0.0;
        String student_name = null ;
        Enumeration en = courseRecords.elements();
        System.out.println("Students that can practice in final exam");
        while (en.hasMoreElements()) {
            CourseRecord cr = (CourseRecord) en.nextElement();
            if (cr.canTakeFinalExam()) {
                System.out.println(cr.getStudent().getName());
            }
        }

the CourseRecord Class


 public double average() throws NotYetSetException {
        double average = 0.0 ;
        double marks = 0.0 ;
        int assignment_count = 0 ;
        Enumeration en = assignments.elements();
        while (en.hasMoreElements()) {
            Assignment assignment = (Assignment) en.nextElement();
            if (assignment.getMark() != -1) {
                assignment_count ++;
                marks += assignment.getMark();
                average = marks/assignment_count;
            }
        }
        return average;
    }

 public boolean canTakeFinalExam() throws NotYetSetException {
        int assignment_count = 0 ;
        Enumeration en = assignments.elements();
        while (en.hasMoreElements()) {
            Assignment assignment = (Assignment) en.nextElement();
            if (assignment.getMark() != -1) {
                assignment_count++;
            }
        }
        return assignment_count>=3 ;
    }































