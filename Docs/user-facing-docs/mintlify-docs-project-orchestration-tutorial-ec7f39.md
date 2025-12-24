I'll analyze the source code to create comprehensive user-facing documentation for the Project Orchestration Tutorial. Let me start by exploring the project structure.

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | grep -E "(project|orchestr)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="output">
./src/app/product/projects/page.tsx
./src/app/product/projects/[id]/page.tsx
./src/components/project/project-card.tsx
./src/components/project/project-list.tsx
./src/components/project/create-project-dialog.tsx
./src/lib/actions/projects.ts
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" \) | head -50</parameter>
</invoke>
</function_calls>
<parameter name="output">
./.next/types/app/api/auth/[...nextauth]/route.ts
./.next/types/app/layout.ts
./.next/types/app/product/page.ts
./.next/types/app/product/settings/page.ts
./.next/types/app/product/projects/page.ts
./.next/types/app/product/projects/[id]/page.ts
./.next/types/app/product/tests/page.ts
./.next/types/app/product/dashboard/page.ts
./.next/types/app/product/layout.ts
./.next/types/app/page.ts
./src/app/api/auth/[...nextauth]/route.ts
./src/app/layout.tsx
./src/app/page.tsx
./src/app/product/page.tsx
./src/app/product/layout.tsx
./src/app/product/dashboard/page.tsx
./src/app/product/settings/page.tsx
./src/app/product/projects/page.tsx
./src/app/product/projects/[id]/page.tsx
./src/app/product/tests/page.tsx
./src/components/auth/login-form.tsx
./src/components/auth/signup-form.tsx
./src/components/navigation/sidebar.tsx
./src/components/navigation/navbar.tsx
./src/components/project/project-card.tsx
./src/components/project/project-list.tsx
./src/components/project/create-project-dialog.tsx
./src/components/test/test-generator.tsx
./src/components/test/test-list.tsx
./src/lib/actions/projects.ts
./src/lib/actions/tests.ts
./src/lib/db/schema.ts
./src/lib/auth/auth-options.ts
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/product/projects/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">import { ProjectList } from '@/components/project/project-list';
import { CreateProjectDialog } from '@/components/project/create-project-dialog';

export default function ProjectsPage() {
  return (
    <div className="container mx-auto py-8">
      <div className="flex justify-between items-center mb-8">
        <h1 className="text-3xl font-bold">Projects</h1>
        <CreateProjectDialog />
      </div>
      <ProjectList />
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/product/projects/[id]/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">import { getProject } from '@/lib/actions/projects';
import { TestGenerator } from '@/components/test/test-generator';
import { TestList } from '@/components/test/test-list';
import { notFound } from 'next/navigation';

export default async function ProjectDetailPage({ params }: { params: { id: string } }) {
  const project = await getProject(params.id);
  
  if (!project) {
    notFound();
  }

  return (
    <div className="container mx-auto py-8">
      <div className="mb-8">
        <h1 className="text-3xl font-bold mb-2">{project.name}</h1>
        <p className="text-gray-600">{project.description}</p>
      </div>
      
      <div className="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-8">
        <div>
          <h2 className="text-2xl font-semibold mb-4">Generate Tests</h2>
          <TestGenerator projectId={project.id} />
        </div>
        <div>
          <h2 className="text-2xl font-semibold mb-4">Project Details</h2>
          <div className="bg-white rounded-lg shadow p-6">
            <div className="space-y-4">
              <div>
                <p className="text-sm text-gray-500">Repository URL</p>
                <p className="font-medium">{project.repositoryUrl}</p>
              </div>
              <div>
                <p className="text-sm text-gray-500">Framework</p>
                <p className="font-medium">{project.framework}</p>
              </div>
              <div>
                <p className="text-sm text-gray-500">Created</p>
                <p className="font-medium">{new Date(project.createdAt).toLocaleDateString()}</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div>
        <h2 className="text-2xl font-semibold mb-4">Test History</h2>
        <TestList projectId={project.id} />
      </div>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/project/create-project-dialog.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useState } from 'react';
import { createProject } from '@/lib/actions/projects';
import { useRouter } from 'next/navigation';

export function CreateProjectDialog() {
  const [isOpen, setIsOpen] = useState(false);
  const [isLoading, setIsLoading] = useState(false);
  const router = useRouter();

  const handleSubmit = async (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    setIsLoading(true);

    const formData = new FormData(e.currentTarget);
    const data = {
      name: formData.get('name') as string,
      description: formData.get('description') as string,
      repositoryUrl: formData.get('repositoryUrl') as string,
      framework: formData.get('framework') as string,
    };

    try {
      const project = await createProject(data);
      setIsOpen(false);
      router.push(`/product/projects/${project.id}`);
      router.refresh();
    } catch (error) {
      console.error('Failed to create project:', error);
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <>
      <button
        onClick={() => setIsOpen(true)}
        className="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700"
      >
        New Project
      </button>

      {isOpen && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
          <div className="bg-white rounded-lg p-8 max-w-md w-full">
            <h2 className="text-2xl font-bold mb-6">Create New Project</h2>
            
            <form onSubmit={handleSubmit} className="space-y-4">
              <div>
                <label className="block text-sm font-medium mb-2">
                  Project Name
                </label>
                <input
                  type="text"
                  name="name"
                  required
                  className="w-full px-3 py-2 border border-gray-300 rounded-lg"
                  placeholder="My Awesome Project"
                />
              </div>

              <div>
                <label className="block text-sm font-medium mb-2">
                  Description
                </label>
                <textarea
                  name="description"
                  rows={3}
                  className="w-full px-3 py-2 border border-gray-300 rounded-lg"
                  placeholder="A brief description of your project"
                />
              </div>

              <div>
                <label className="block text-sm font-medium mb-2">
                  Repository URL
                </label>
                <input
                  type="url"
                  name="repositoryUrl"
                  required
                  className="w-full px-3 py-2 border border-gray-300 rounded-lg"
                  placeholder="https://github.com/username/repo"
                />
              </div>

              <div>
                <label className="block text-sm font-medium mb-2">
                  Framework
                </label>
                <select
                  name="framework"
                  required
                  className="w-full px-3 py-2 border border-gray-300 rounded-lg"
                >
                  <option value="">Select a framework</option>
                  <option value="react">React</option>
                  <option value="vue">Vue</option>
                  <option value="angular">Angular</option>
                  <option value="nextjs">Next.js</option>
                  <option value="other">Other</option>
                </select>
              </div>

              <div className="flex justify-end gap-4 mt-6">
                <button
                  type="button"
                  onClick={() => setIsOpen(false)}
                  className="px-4 py-2 text-gray-700 hover:bg-gray-100 rounded-lg"
                  disabled={isLoading}
                >
                  Cancel
                </button>
                <button
                  type="submit"
                  className="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 disabled:opacity-50"
                  disabled={isLoading}
                >
                  {isLoading ? 'Creating...' : 'Create Project'}
                </button>
              </div>
            </form>
          </div>
        </div>
      )}
    </>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/project/project-list.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useEffect, useState } from 'react';
import { getProjects } from '@/lib/actions/projects';
import { ProjectCard } from './project-card';

interface Project {
  id: string;
  name: string;
  description: string;
  repositoryUrl: string;
  framework: string;
  createdAt: Date;
}

export function ProjectList() {
  const [projects, setProjects] = useState<Project[]>([]);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    async function loadProjects() {
      try {
        const data = await getProjects();
        setProjects(data);
      } catch (error) {
        console.error('Failed to load projects:', error);
      } finally {
        setIsLoading(false);
      }
    }

    loadProjects();
  }, []);

  if (isLoading) {
    return <div className="text-center py-12">Loading projects...</div>;
  }

  if (projects.length === 0) {
    return (
      <div className="text-center py-12">
        <p className="text-gray-600 mb-4">No projects yet</p>
        <p className="text-sm text-gray-500">Create your first project to get started</p>
      </div>
    );
  }

  return (
    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      {projects.map((project) => (
        <ProjectCard key={project.id} project={project} />
      ))}
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/project/project-card.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import Link from 'next/link';

interface ProjectCardProps {
  project: {
    id: string;
    name: string;
    description: string;
    repositoryUrl: string;
    framework: string;
    createdAt: Date;
  };
}

export function ProjectCard({ project }: ProjectCardProps) {
  return (
    <Link href={`/product/projects/${project.id}`}>
      <div className="bg-white rounded-lg shadow hover:shadow-lg transition-shadow p-6 cursor-pointer">
        <h3 className="text-xl font-semibold mb-2">{project.name}</h3>
        <p className="text-gray-600 text-sm mb-4 line-clamp-2">
          {project.description || 'No description'}
        </p>
        <div className="flex items-center justify-between text-sm">
          <span className="bg-blue-100 text-blue-800 px-2 py-1 rounded">
            {project.framework}
          </span>
          <span className="text-gray-500">
            {new Date(project.createdAt).toLocaleDateString()}
          </span>
        </div>
      </div>
    </Link>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/test/test-generator.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useState } from 'react';
import { generateTests } from '@/lib/actions/tests';
import { useRouter } from 'next/navigation';

interface TestGeneratorProps {
  projectId: string;
}

export function TestGenerator({ projectId }: TestGeneratorProps) {
  const [isGenerating, setIsGenerating] = useState(false);
  const [testType, setTestType] = useState('unit');
  const [componentPath, setComponentPath] = useState('');
  const router = useRouter();

  const handleGenerate = async (e: React.FormEvent) => {
    e.preventDefault();
    setIsGenerating(true);

    try {
      await generateTests({
        projectId,
        testType,
        componentPath,
      });
      router.refresh();
      setComponentPath('');
    } catch (error) {
      console.error('Failed to generate tests:', error);
    } finally {
      setIsGenerating(false);
    }
  };

  return (
    <div className="bg-white rounded-lg shadow p-6">
      <form onSubmit={handleGenerate} className="space-y-4">
        <div>
          <label className="block text-sm font-medium mb-2">
            Test Type
          </label>
          <select
            value={testType}
            onChange={(e) => setTestType(e.target.value)}
            className="w-full px-3 py-2 border border-gray-300 rounded-lg"
          >
            <option value="unit">Unit Tests</option>
            <option value="integration">Integration Tests</option>
            <option value="e2e">End-to-End Tests</option>
          </select>
        </div>

        <div>
          <label className="block text-sm font-medium mb-2">
            Component Path
          </label>
          <input
            type="text"
            value={componentPath}
            onChange={(e) => setComponentPath(e.target.value)}
            placeholder="src/components/Button.tsx"
            className="w-full px-3 py-2 border border-gray-300 rounded-lg"
            required
          />
          <p className="text-xs text-gray-500 mt-1">
            Enter the path to the component you want to test
          </p>
        </div>

        <button
          type="submit"
          disabled={isGenerating}
          className="w-full bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 disabled:opacity-50"
        >
          {isGenerating ? 'Generating...' : 'Generate Tests'}
        </button>
      </form>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/test/test-list.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useEffect, useState } from 'react';
import { getTests } from '@/lib/actions/tests';

interface Test {
  id: string;
  projectId: string;
  testType: string;
  componentPath: string;
  status: string;
  generatedCode: string;
  createdAt: Date;
}

interface TestListProps {
  projectId: string;
}

export function TestList({ projectId }: TestListProps) {
  const [tests, setTests] = useState<Test[]>([]);
  const [isLoading, setIsLoading] = useState(true);
  const [selectedTest, setSelectedTest] = useState<Test | null>(null);

  useEffect(() => {
    async function loadTests() {
      try {
        const data = await getTests(projectId);
        setTests(data);
      } catch (error) {
        console.error('Failed to load tests:', error);
      } finally {
        setIsLoading(false);
      }
    }

    loadTests();
  }, [projectId]);

  if (isLoading) {
    return <div className="text-center py-8">Loading tests...</div>;
  }

  if (tests.length === 0) {
    return (
      <div className="text-center py-8 bg-white rounded-lg shadow">
        <p className="text-gray-600">No tests generated yet</p>
        <p className="text-sm text-gray-500 mt-2">Generate your first test to get started</p>
      </div>
    );
  }

  return (
    <div className="space-y-4">
      {tests.map((test) => (
        <div key={test.id} className="bg-white rounded-lg shadow p-6">
          <div className="flex justify-between items-start mb-4">
            <div>
              <h3 className="font-semibold">{test.componentPath}</h3>
              <p className="text-sm text-gray-500">
                {test.testType} • {new Date(test.createdAt).toLocaleDateString()}
              </p>
            </div>
            <span
              className={`px-3 py-1 rounded text-sm ${
                test.status === 'completed'
                  ? 'bg-green-100 text-green-800'
                  : test.status === 'failed'
                  ? 'bg-red-100 text-red-800'
                  : 'bg-yellow-100 text-yellow-800'
              }`}
            >
              {test.status}
            </span>
          </div>

          {selectedTest?.id === test.id ? (
            <div>
              <pre className="bg-gray-100 p-4 rounded-lg overflow-x-auto text-sm">
                <code>{test.generatedCode}</code>
              </pre>
              <button
                onClick={() => setSelectedTest(null)}
                className="mt-4 text-blue-600 hover:text-blue-700 text-sm"
              >
                Hide Code
              </button>
            </div>
          ) : (
            <button
              onClick={() => setSelectedTest(test)}
              className="text-blue-600 hover:text-blue-700 text-sm"
            >
              View Generated Code
            </button>
          )}
        </div>
      ))}
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/lib/actions/projects.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">'use server';

import { db } from '@/lib/db';
import { projects } from '@/lib/db/schema';
import { eq } from 'drizzle-orm';
import { getServerSession } from 'next-auth';
import { authOptions } from '@/lib/auth/auth-options';

export async function createProject(data: {
  name: string;
  description: string;
  repositoryUrl: string;
  framework: string;
}) {
  const session = await getServerSession(authOptions);
  
  if (!session?.user?.id) {
    throw new Error('Unauthorized');
  }

  const [project] = await db
    .insert(projects)
    .values({
      ...data,
      userId: session.user.id,
    })
    .returning();

  return project;
}

export async function getProjects() {
  const session = await getServerSession(authOptions);
  
  if (!session?.user?.id) {
    throw new Error('Unauthorized');
  }

  const userProjects = await db
    .select()
    .from(projects)
    .where(eq(projects.userId, session.user.id));

  return userProjects;
}

export async function getProject(id: string) {
  const session = await getServerSession(authOptions);
  
  if (!session?.user?.id) {
    throw new Error('Unauthorized');
  }

  const [project] = await db
    .select()
    .from(projects)
    .where(eq(projects.id, id));

  if (!project || project.userId !== session.user.id) {
    return null;
  }

  return project;
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/lib/actions/tests.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">'use server';

import { db } from '@/lib/db';
import { tests } from '@/lib/db/schema';
import { eq } from 'drizzle-orm';
import { getServerSession } from 'next-auth';
import { authOptions } from '@/lib/auth/auth-options';

export async function generateTests(data: {
  projectId: string;
  testType: string;
  componentPath: string;
}) {
  const session = await getServerSession(authOptions);
  
  if (!session?.user?.id) {
    throw new Error('Unauthorized');
  }

  // Simulate test generation
  const generatedCode = `
import { render, screen } from '@testing-library/react';
import Component from '${data.componentPath}';

describe('${data.componentPath}', () => {
  it('should render correctly', () => {
    render(<Component />);
    expect(screen.getByRole('button')).toBeInTheDocument();
  });
});
  `.trim();

  const [test] = await db
    .insert(tests)
    .values({
      projectId: data.projectId,
      testType: data.testType,
      componentPath: data.componentPath,
      status: 'completed',
      generatedCode,
    })
    .returning();

  return test;
}

export async function getTests(projectId: string) {
  const session = await getServerSession(authOptions);
  
  if (!session?.user?.id) {
    throw new Error('Unauthorized');
  }

  const projectTests = await db
    .select()
    .from(tests)
    .where(eq(tests.projectId, projectId));

  return projectTests;
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/lib/db/schema.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">import { pgTable, text, timestamp, uuid } from 'drizzle-orm/pg-core';

export const users = pgTable('users', {
  id: uuid('id').defaultRandom().primaryKey(),
  email: text('email').notNull().unique(),
  name: text('name'),
  password: text('password').notNull(),
  createdAt: timestamp('created_at').defaultNow().notNull(),
});

export const projects = pgTable('projects', {
  id: uuid('id').defaultRandom().primaryKey(),
  userId: uuid('user_id').notNull().references(() => users.id),
  name: text('name').notNull(),
  description: text('description'),
  repositoryUrl: text('repository_url').notNull(),
  framework: text('framework').notNull(),
  createdAt: timestamp('created_at').defaultNow().notNull(),
});

export const tests = pgTable('tests', {
  id: uuid('id').defaultRandom().primaryKey(),
  projectId: uuid('project_id').notNull().references(() => projects.id),
  testType: text('test_type').notNull(),
  componentPath: text('component_path').notNull(),
  status: text('status').notNull(),
  generatedCode: text('generated_code').notNull(),
  createdAt: timestamp('created_at').defaultNow().notNull(),
});
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/navigation/sidebar.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import Link from 'next/link';
import { usePathname } from 'next/navigation';

export function Sidebar() {
  const pathname = usePathname();

  const links = [
    { href: '/product/dashboard', label: 'Dashboard' },
    { href: '/product/projects', label: 'Projects' },
    { href: '/product/tests', label: 'Tests' },
    { href: '/product/settings', label: 'Settings' },
  ];

  return (
    <aside className="w-64 bg-white border-r border-gray-200 min-h-screen">
      <nav className="p-4">
        <ul className="space-y-2">
          {links.map((link) => (
            <li key={link.href}>
              <Link
                href={link.href}
                className={`block px-4 py-2 rounded-lg ${
                  pathname === link.href
                    ? 'bg-blue-100 text-blue-700'
                    : 'text-gray-700 hover:bg-gray-100'
                }`}
              >
                {link.label}
              </Link>
            </li>
          ))}
        </ul>
      </nav>
    </aside>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/product/dashboard/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">import { getProjects } from '@/lib/actions/projects';

export default async function DashboardPage() {
  const projects = await getProjects();

  return (
    <div className="container mx-auto py-8">
      <h1 className="text-3xl font-bold mb-8">Dashboard</h1>
      
      <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-sm text-gray-500 mb-2">Total Projects</h3>
          <p className="text-3xl font-bold">{projects.length}</p>
        </div>
        
        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-sm text-gray-500 mb-2">Active Tests</h3>
          <p className="text-3xl font-bold">0</p>
        </div>
        
        <div className="bg-white rounded-lg shadow p-6">
          <h3 className="text-sm text-gray-500 mb-2">Test Coverage</h3>
          <p className="text-3xl font-bold">0%</p>
        </div>
      </div>

      <div className="bg-white rounded-lg shadow p-6">
        <h2 className="text-xl font-semibold mb-4">Recent Activity</h2>
        <p className="text-gray-600">No recent activity</p>
      </div>
    </div>
  );
}
</parameter>

Now let me create comprehensive user-facing documentation for the Project Orchestration Tutorial:

<function_calls>
<invoke name="execute_command">
<parameter name="command">mkdir -p user-facing-docs</parameter>
</invoke>
</function_calls>
<parameter name="output"></parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">basename $(pwd)</parameter>
</invoke>
</function_calls>
<parameter name="output">project</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">cat > user-facing-docs/project-orchestration-tutorial.md << 